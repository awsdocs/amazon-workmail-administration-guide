# Configuring AWS Lambda for Amazon WorkMail<a name="lambda"></a>

Use the **Run Lambda** inbound and outbound email flow rules to pass emails that match the rules to a Lambda function for processing\.

When you use the **Run Lambda** rule for inbound emails, incoming emails that match the rule are passed to a Lambda function for processing before the emails are delivered to users' mailboxes\.

When you use the **Run Lambda** rule for outbound emails, outbound emails that match the rule are passed to a Lambda function for processing at the same time that the email is sent\.

The Lambda function does not affect the sending or receiving of email\. For more information about inbound and outbound email flow rules, see [Managing Email Flows](email-flows.md)\. For more information about Lambda, see the [https://docs.aws.amazon.com/lambda/latest/dg/welcome.html](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)\.

**Note**  
Currently, Lambda email flow rules reference only Lambdas in the same AWS Region and AWS account as the Amazon WorkMail organization being configured\.

## Getting Started with Lambda for Amazon WorkMail<a name="start-lambda"></a>

To start using Lambda with Amazon WorkMail, deploy [the example Lambda function](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:489970191081:applications/workmail-hello-world-python) from the AWS Serverless Application Repository to your account\. Permissions for the example Lambda function are already configured for you\.

If you choose to create your own Lambda function to use with Amazon WorkMail, you must configure permissions using the AWS Command Line Interface \(AWS CLI\)\. In the following example command, replace `MY_FUNCTION_NAME` with the name of your Lambda function, and replace `REGION` with your Amazon WorkMail Region\. Available Amazon WorkMail Regions include `us-east-1`, `us-west-2`, and `eu-west-1`\.

```
aws --region REGION lambda add-permission --function-name MY_FUNCTION_NAME --statement-id AllowWorkMail --action "lambda:InvokeFunction" --principal workmail.REGION.amazonaws.com
```

For more information about using the AWS CLI, see the [https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)\.

## Lambda Event Data<a name="lambda-data"></a>

The Lambda function is triggered using the following event data\. The presentation of the data varies depending on which programming language is used for the Lambda function\.

```
{
    "summaryVersion": "2018-10-10",
    "envelope": {
        "mailFrom" : {
            "address" : "from@example.com"
        },
        "recipients" : [
           { "address" : "recipient1@example.com" },
           { "address" : "recipient2@example.com" }
        ]
    },
    "sender" : {
        "address" :  "sender@example.com"
    },
    "subject" : "Hello From Amazon WorkMail!",
    "truncated": false
}
```

The event JSON includes the following data\.

**envelope**  
The envelope of the email message, which includes the following fields:    
**mailFrom**  
The **From** address, which is usually the email address of the user who sent the message\. If the user sent the message as another user or on behalf of another user, the **mailFrom** field returns the email address of the user on whose behalf the email was sent, not the email address of the actual sender\.  
**recipients**  
A list of recipient email addresses\. There is no distinction between **To**, **CC**, or **BCC**\.  
For inbound email flow rules, this list includes recipients for each domain that is part of the Amazon WorkMail organization in which the rule is created\. The Lambda function is invoked separately for each SMTP conversation from the sender, and the contents of the recipients field match the recipients from that SMTP conversation\. Recipients with external domains are not included\.

**sender**  
The email address of the user who sent the email message on behalf of another user\. This field is set only when an email is sent on behalf of another user\.

**subject**  
The email subject line\. Truncated when it exceeds the 256 character limit\.

**truncated**  
Applies to the payload size, not the subject line length\. When `true`, the payload size exceeds the 128 KB limit, so the list of recipients is truncated in order to meet the limit\.

## More Information about Using Lambda with Amazon WorkMail<a name="lambda-more"></a>

You can also access the full content of the email message that triggers the Lambda\. For more information, see [Retrieving Message Content with AWS Lambda](lambda-content.md)\. 