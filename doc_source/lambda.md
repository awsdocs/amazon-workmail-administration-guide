# Configuring AWS Lambda for Amazon WorkMail<a name="lambda"></a>

Use the **Run Lambda** outbound email flow rule to pass rule\-matching emails to a Lambda function for processing after the email is sent\. When you use the **Run Lambda** rule, it sends the email and triggers the Lambda function at the same time\. The Lambda function does not affect the sending of the email\. For more information about outbound email flow rules, see [Outbound Email Rule Actions](email-flows.md#email-flows-rule-outbound)\. For more information about Lambda, see the [https://docs.aws.amazon.com/lambda/latest/dg/welcome.html](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)\.

**Note**  
Currently, Lambda email flow rules reference only Lambdas in the same AWS Region and AWS account as the Amazon WorkMail organization being configured\.

To start using Lambda with Amazon WorkMail, deploy [the example Lambda function](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:489970191081:applications/workmail-hello-world-python) from the AWS Serverless Application Repository to your account\. Permissions for the example Lambda function are already configured for you\.

If you choose to create your own Lambda function to use with Amazon WorkMail, you must configure permissions using the AWS Command Line Interface \(AWS CLI\)\. In the following example command, replace `MY_FUNCTION_NAME` with the name of your Lambda function, and replace `REGION` with your Amazon WorkMail region\. Available Amazon WorkMail regions include `us-east-1`, `us-west-2`, and `eu-west-1`\.

```
aws --region REGION lambda add-permission --function-name MY_FUNCTION_NAME --statement-id AllowWorkMail --action "lambda:InvokeFunction" --principal workmail.REGION.amazonaws.com
```

For more information about using the AWS CLI, see the [https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)\.

The Lambda function is triggered using the following event data\. The presentation of the data varies depending on which programming language is used for the Lambda function\.

```
{
    "summaryVersion": "2018-10-10",
    "envelope": {
        "mailFrom" : {
            "address" : "from@domain.test"
        },
        "recipients" : [
           { "address" : "recipient1@domain.test" },
           { "address" : "recipient2@domain.test" }
        ]
    },
    "sender" : {
        "address" :  "sender@domain.test"
    },
    "subject" : "Hello From Amazon WorkMail!",
    "truncated": false
}
```

The event JSON includes the following data\.

**envelope**  
The SMTP envelope of the email message, which includes the following fields:    
**mailFrom**  
The **From** address in the SMTP conversation\. It is usually the email address of the user who sent the message\. If the user sent the message as another user or on behalf of another user, the **mailFrom** field returns the email address of the user on whose behalf the email was sent, not the email address of the actual sender\.  
**recipients**  
The list of all recipient email addresses\. There is no distinction between **To**, **CC**, or **BCC**\.

**sender**  
The email address of the user who sent the email message on behalf of another user\. This field is set only when an email is sent on behalf of another user\.

**subject**  
The email subject line\.

**truncated**  
When `true`, the payload size exceeds the 128 KB limit, so the list of recipients is truncated in order to meet the limit\.