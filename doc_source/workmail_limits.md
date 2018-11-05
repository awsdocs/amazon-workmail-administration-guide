# Amazon WorkMail Limits<a name="workmail_limits"></a>

Amazon WorkMail can be used by enterprise customers as well as small business owners\. Although we support most use cases without the need to configure any changes in limits, we also protect our users and the internet against abuse of the product\. Therefore, some customers may run into limits that we have set\. This section describes these limits and how to change them\.

Some limit values can be changed, and some are hard limits that cannot be changed\. If you want to change a limit value for Amazon WorkMail, follow these steps to submit a limit increase request:

1. Go to the AWS Support Center, sign in if prompted, and then choose **Create Case**\.

1. Under **Regarding**, choose **Service Limit Increase**\.

1. Under **Limit Type**, choose the type of limit to increase, fill in the necessary form fields, and then choose your preferred method of contact\.

1. If you are requesting a limit increase for a specific organization, enter the **Organization Alias**\.

1. Wait up to five working days for increases to become effective\.

**Note**  
It is possible to request a limit increase regardless of the age of the account\. When you create a new AWS account, the values you are subjected to are usually lower than those for veteran accounts\. On this page, only the default limit values for veteran accounts are listed\.

## Amazon WorkMail Organization and User Limits<a name="user_limits"></a>

You can add up to 25 users for a 30\-day free trial\. After this period ends, you are charged for all active users unless you remove them or close your Amazon WorkMail account\.

All messages that are sent to another user are considered when evaluating these limits\. These include emails, meeting requests, meeting responses, task requests, and messages that are forwarded or redirected automatically as the result of a rule\.

**Note**  
When requesting a limit increase request only for a specific organization, include the organization name in your request\.


| Resource | Default Limit  | Upper Bound for Change Requests  | 
| --- | --- | --- | 
|  Users per Amazon WorkMail organization  |  1,000  |  Can be increased depending on the directory type that is used for the organization: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/workmail/latest/adminguide/workmail_limits.html) \*If you are using Simple AD or AD Connector, see [AWS Directory Service](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/what_is.html) for additional information\.  | 
| Free trial users |  Up to 25 users in the first 30 days  |  The free trial period is only applicable for the first 25 users in any organization\. Any additional users are not included in the free trial offer\.  | 
| Recipients addressed per AWS account per day  | 100,000 recipients external to the organization, with no hard limit on recipients internal to the organization | There is no upper bound\. However, Amazon WorkMail is a business email service and not intended to be used for bulk email services\. For bulk email services, see [Amazon SES](https://aws.amazon.com/ses/) or [Amazon Pinpoint](https://aws.amazon.com/pinpoint/)\. | 
| Recipients addressed per AWS account per day using any of the test domains | 200 recipients, regardless of destination | There is no upper bound\. However, the test mail domain is not intended for long\-term usage\. Instead, we recommend that you add your own domain and use it as the default domain\. | 

## WorkMail Organization Setting Limits<a name="organization_limits"></a>


| Resource | Default Limit | 
| --- | --- | 
| Number of domains per Amazon WorkMail organization | 1,000This is a hard limit and cannot be changed\.  | 
|  Number of sender patterns in email flow rules per rule  |  250 This is a hard limit and cannot be changed\.  | 
|  Number of sender patterns in email flow rules per organization  |  1,000 This is a hard limit and cannot be changed\.  | 

## Per\-User Limits<a name="per_user_limits"></a>

All messages that are sent to another user are considered when evaluating these limits\. These include emails, meeting requests, meeting responses, task requests, and messages that are forwarded or redirected automatically as the result of a rule\.


| Resource | Default Limit | Upper Limit for Change Requests | 
| --- | --- | --- | 
| Maximum size of mailbox | 50 GB |  50 GB  | 
| Maximum number of aliases per user |  100 This is a hard limit and cannot be changed\.  |  N/A  | 
| Recipients addressed per user per day using the domain that you own | 10,000 recipients external to the organization, with no hard limit on recipients internal to the organization\. | There is no upper bound\. However, Amazon WorkMail is a business email service and not intended to be used for bulk email services\. For bulk email services, see [Amazon SES](https://aws.amazon.com/ses/) or [Amazon Pinpoint](https://aws.amazon.com/pinpoint/)\. | 

## Message Limits<a name="message_limits"></a>

All messages that are sent to another user are considered when evaluating these limits\. These include emails, meeting requests, meeting responses, task requests, and messages that are forwarded or redirected automatically as the result of a rule\.


| Resource  | Default Limit  | 
| --- | --- | 
|  Maximum size of incoming message  | 25 MBThis is a hard limit and cannot be changed\. | 
| Maximum size of outgoing message | 25 MBThis is a hard limit and cannot be changed\. | 
|  Number of recipients per message  | 500This is a hard limit and cannot be changed\. | 