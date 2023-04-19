# Building a Custom Availability Provider Lambda function<a name="building_cap"></a>

Custom Availability Providers \(CAPs\) are configured with a JSON\-based request and response protocol that is written in a well defined JSON schema\. A Lambda function will parse the request and provide a valid response\.

**Topics**
+ [Request and response elements](#cap_request_response_elements)
+ [Granting access](#granting_access)
+ [Example of Amazon WorkMail using a CAP Lambda function](#cap_example_github)

## Request and response elements<a name="cap_request_response_elements"></a>

### Request elements<a name="cap_request"></a>

The following is a sample request used to configure a CAP for an Amazon WorkMail user: 

```
{
    "requester": {
        "email": "user1@internal.example.com",
        "userName": "user1",
        "organization": "m-0123456789abcdef0123456789abcdef",
        "userId": "S-1-5-18",
        "origin": "127.0.0.1"
    },
    "mailboxes": [
        "user2@external.example.com",
        "unknown@internal.example.com"
    ],
    "window": {
        "startDate": "2021-05-04T00:00:00.000Z",
        "endDate": "2021-05-06T00:00:00.000Z"
    }
}
```

A request is composed of three sections: **requester**, **mailboxes**, and **window**\. These are described in the following [Requester](#cap_request_requester), [Mailboxes](#cap_request_mailboxes), and [Window](#cap_request_window) sections of this guide\.

#### Requester<a name="cap_request_requester"></a>

The *requester* section provides information about the user who made the original request to Amazon WorkMail\. CAPs use this information to change the behavior of the provider\. For instance, this data can be used to impersonate the same user on the backend availability provider or certain details can be omitted from the response\.


| Field | Description | Required | 
| --- | --- | --- | 
|  `Email`  |  The primary email address of the requester\.  |  Yes  | 
|  `Username`  |  The user name of the requester\.  |  Yes  | 
|  `Organization`  |  The organization ID of the requester\.  |  Yes  | 
|  `UserID`  |  The requester ID\.  |  Yes  | 
|  `Origin`  |  The remote address of the request\.  |  No  | 
|  `Bearer`  |  Reserved for future use\.  |  No  | 

#### Mailboxes<a name="cap_request_mailboxes"></a>

The *mailboxes* section contains a comma separated list of email addresses of users for which availability information is requested\.

#### Window<a name="cap_request_window"></a>

The *window* section contains the time window which the availability information is requested for\. Both `startDate` and `endDate` are specified in UTC and are formatted according to [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339)\. Events aren't expected to be truncated\. In other words, if an event starts before the defined `StartDate`, the original start will be used\.

### Response elements<a name="cap_response"></a>

Amazon WorkMail will wait for 25 seconds to get a response from the CAP Lambda function\. After 25 seconds, Amazon WorkMail will assume the function has failed and generate failures for the associated mailboxes in the EWS GetUserAvailability response\. This will not cause the entire GetUserAvailability operation to fail\.

The following is a sample response from the configuration defined at the beginning of this section: 

```
{
    "mailboxes": [{
        "mailbox": "user2@external.example.com",
        "events": [{
            "startTime": "2021-05-03T23:00:00.000Z",
            "endTime": "2021-05-04T03:00:00.000Z",
            "busyType": "BUSY"|"FREE"|"TENTATIVE",
            "details": {  // optional
                "subject": "Late meeting",
                "location": "Chime",
                "instanceType": "SINGLE_INSTANCE"|"RECURRING_INSTANCE"|"EXCEPTION",
                "isMeeting": true,
                "isReminderSet": true,
                "isPrivate": false
            }
        }],
        "workingHours": {
            "timezone": {
                "name": "W. Europe Standard Time"
                "bias": 60,
                "standardTime": {  // optional (not needed for fixed offsets)
                    "offset": 60,
                    "time": "02:00:00",
                    "month": "JAN"|"FEB"|"MAR"|"APR"|"JUN"|"JUL"|"AUG"|"SEP"|"OCT"|"NOV"|"DEC",
                    "week": "FIRST"|"SECOND"|"THIRD"|"FOURTH"|"LAST",
                    "dayOfWeek": "SUN"|"MON"|"TUE"|"WED"|"THU"|"FRI"|"SAT"
                },
                "daylightTime": {  // optional (not needed for fixed offsets)
                    "offset": 0,
                    "time": "03:00:00",
                    "month": "JAN"|"FEB"|"MAR"|"APR"|"JUN"|"JUL"|"AUG"|"SEP"|"OCT"|"NOV"|"DEC",
                    "week": "FIRST"|"SECOND"|"THIRD"|"FOURTH"|"LAST",
                    "dayOfWeek": "SUN"|"MON"|"TUE"|"WED"|"THU"|"FRI"|"SAT"
                },                
            },
            "workingPeriods":[{
                "startMinutes": 480,
                "endMinutes": 1040,
                "days": ["SUN"|"MON"|"TUE"|"WED"|"THU"|"FRI"|"SAT"]
            }]
        }
    },{
        "mailbox": "unknown@internal.example.com",
        "error": "MailboxNotFound"
    }]
}
```

A response is composed of a single *mailboxes* section which consists of a list of mailboxes\. Each mailbox for which availability is successfully obtained is composed of three sections: *mailbox*, *events*, and *workinghours*\. If the availability provider has failed to obtain availability information for a mailbox, the section is composed of two sections: *mailbox* and *error*\. These are described in the following [Mailbox](#cap_response_mailbox), [Events](#cap_response_events), [Working Hours](#cap_response_workinghours), [Timezone](#cap_response_timezone), [Working Periods](#cap_response_workingperiods), and [Error](#cap_response_error) sections of this guide\.

#### Mailbox<a name="cap_response_mailbox"></a>

The *mailbox* section is the email address of the user found in the *mailboxes* section of the request\.

#### Events<a name="cap_response_events"></a>

The *events* section is a list of events that occur in the requested window\. Each event is defined with the following parameters:


| Field | Description | Required | 
| --- | --- | --- | 
|  `startTime`  |  The start time of the event in UTC and formatted according to [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339)\.  |  Yes  | 
|  `endTime`  |  The end time of the event in UTC and formatted according to [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339)\.  |  Yes  | 
|  `busyType`  |  The busy type of the event\. Can be `Busy`, `Free`, or `Tentative`\.  |  Yes  | 
|  `details`  |  The details of the event\.  |  No  | 
|  `details.subject`  |  The subject of the event\.  |  Yes  | 
|  `details.location`  |  The location of the event\.  |  Yes  | 
|  `details.instanceType`  |  The instance type of the event\. Can be `Single_Instance`, `Recurring_Instance`, or `Exception`\.  |  Yes  | 
|  `details.isMeeting`  |  A Boolean to indicate if the event has attendees\.  |  Yes  | 
|  `details.isReminderSet`  |  A Boolean to indicate if the event has a reminder set\.  |  Yes  | 
|  `details.isPrivate`  |  A Boolean to indicate if the event is set to private\.  |  Yes  | 

#### Working Hours<a name="cap_response_workinghours"></a>

The *workingHours* section contains information about the the mailbox owner's working hours\. It contains two sections: *timezone* and *workingPeriods*\. 

#### Timezone<a name="cap_response_timezone"></a>

The *timezone* subsection describes the mailbox owner's time zone\. It's important to correctly render the user's working hours when the requester works in a different time zone\. The availability provider is required to explicitly describe the time zone, rather than using a name\. Using the standarized time zone description helps avoid time zone mismatches\.


| Field | Description | Required | 
| --- | --- | --- | 
|  `name`  |  The time zone's name\.  |  Yes  | 
|  `bias`  |  The default offset from GMT in minutes\.  |  Yes  | 
|  `standardTime`  |  The start of standard time for the specified time zone\.  |  No  | 
|  `daylightTime`  |  The start of daylight savings time for the specified time zone\.  |  No  | 

You must either define both `standardTime` and `daylightTime`, or omit both\. Fields in the `standardTime` and `daylightTime` object are:


| Field | Description | Allowed Values | 
| --- | --- | --- | 
|  `offset`  |  The offset relative to the default offset in minutes\.  |  NA  | 
|  `time`  |  The time at which the transition between standard time and daylight savings time happens, specified as `hh:mm:ss`\.  |  NA  | 
|  `month`  |  The month that the transition between standard time and daylight savings time happens\.  |  `JAN`,`FEB`, `MAR`, `APR`, `JUN`, `JUL`, `AUG`, `SEP`, `OCT`, `NOV`, `DEC`  | 
|  `week`  |  The week within the specified month that the transition between standard time and daylight savings time happens\.  |  `FIRST`, `SECOND`, `THIRD`, `FOURTH`, `LAST`  | 
|  `dayOfWeek`  |  The day within the specified week that the transition between standard time and daylight savings time happens\.  |  `SUN`, `MON`, `TUE`, `WED`, `THU`, `FRI`, `SAT`  | 

#### Working Periods<a name="cap_response_workingperiods"></a>

The *workingPeriods* section contains one or more working period objects\. Each period defines a start and end of working day for one or more days\. 


| Field | Description | Allowed Values | 
| --- | --- | --- | 
|  `startMinutes`  |  The start of the working day in minutes from midnight\.  |  NA  | 
|  `endMinutes`  |  The end of the working day in minutes from midnight\.  |  NA  | 
|  `days`  |  The days that this period applies to\.  |  `SUN`, `MON`, `TUE`, `WED`, `THU`, `FRI`, `SAT`  | 

#### Error<a name="cap_response_error"></a>

The *error* field can contain arbitrary error messages\. The following table lists a mapping of well known codes to EWS error codes\. All other messages will be mapped to `ERROR_FREE_BUSY_GENERATION_FAILED`\. 


| Value | EWS Error code | 
| --- | --- | 
|  `MailboxNotFound`  |  `ERROR_MAIL_RECIPIENT_NOT_FOUND`  | 
|  `ErrorAvailabilityConfigNotFound`  |  `ERROR_AVAILABILITY_CONFIG_NOT_FOUND`  | 
|  `ErrorServerBusy`  |  `ERROR_SERVER_BUSY`  | 
|  `ErrorTimeoutExpired`  |  `ERROR_TIMEOUT_EXPIRED`  | 
|  `ErrorFreeBusyGenerationFailed`  |  `ERROR_FREE_BUSY_GENERATION_FAILED`  | 
|  `ErrorResponseSchemaValidation`  |  `ERROR_RESPONSE_SCHEMA_VALIDATION`  | 

## Granting access<a name="granting_access"></a>

Run the following Lambda command from the AWS Command Line Interface \(AWS CLI\)\. This command adds a resource policy to the Lambda function that parses the CAP\. This function allows the Amazon WorkMail availability service to invoke your Lambda function\.

```
aws lambda add-permission \
    --region LAMBDA_REGION \
    --function-name CAP_FUNCTION_NAME \
    --statement-id AllowWorkMail \
    --action "lambda:InvokeFunction" \
    --principal availability.workmail.WM_REGION.amazonaws.com \
    --source-account WM_ACCOUNT_ID \
    --source-arn arn:aws:workmail:WM_REGION:WM_ACCOUNT_ID:organization/ORGANIZATION_ID
```

In the command, add the following parameters where indicated:
+ *LAMBDA\_REGION* — Name of the region where the CAP Lambda is deployed\. For example, `us-east-1`\.
+ *CAP\_FUNCTION\_NAME* — Name of the CAP Lambda function\. 
**Note**  
This can be the name, alias, or either partial or full ARN of the CAP Lambda function\.
+ *WM\_REGION* — Name of the region where the Amazon WorkMail organization invokes the Lambda function\. 
**Note**  
Only the following Regions are available for use with CAP:  
US East \(N\. Virginia\)
US West \(Oregon\)
Europe \(Ireland\)
+ *WM\_ACCOUNT\_ID* — The ID of the Organization account\.
+ *ORGANIZATION\_ID* — The ID of the Organization that invokes the CAP Lambda\. For example, Org ID: m\-934ebb9eb57145d0a6cab566ca81a21f\.

**Note**  
*LAMBDA\_REGION* and *WM\_REGION* will be different only if cross\-Region calls are necessary\. If cross\-Region calls are not necessary, they will be the same\.

## Example of Amazon WorkMail using a CAP Lambda function<a name="cap_example_github"></a>

For an example of Amazon WorkMail using a CAP Lambda function to query an EWS endpoint, see this [AWS sample application](https://github.com/aws-samples/amazon-workmail-lambda-templates/tree/master/workmail-cap-exchange) on the *Serverless applications for Amazon WorkMail GitHub repository*\.