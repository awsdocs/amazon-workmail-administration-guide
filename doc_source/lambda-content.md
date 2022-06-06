# Retrieving message content with AWS Lambda<a name="lambda-content"></a>

After you configure an AWS Lambda function to manage email flows for Amazon WorkMail, you can access the full content of the email messages that are processed using Lambda\. For more information about getting started with Lambda for Amazon WorkMail, see [Configuring AWS Lambda for Amazon WorkMail](lambda.md)\.

To access the full content of email messages, use the `GetRawMessageContent` action in the Amazon WorkMail Message Flow API\. The email message ID that is passed to your Lambda function upon invocation sends a request to the API\. Then, the API responds with the full MIME content of the email message\. For more information, see [Amazon WorkMail Message Flow](https://docs.aws.amazon.com/workmail/latest/APIReference/API_Operations_Amazon_WorkMail_Message_Flow.html) in the *Amazon WorkMail API Reference*\.

The following example shows how a Lambda function using the Python runtime environment can retrieve the full message content\.

**Tip**  
If you start by deploying the Amazon WorkMail [ Hello World Lambda function ](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:489970191081:applications/workmail-hello-world-python) from the AWS Serverless Application Repository to your account, the system creates a Lambda function in your account with all the necessary resources and permission\. You can then add your business logic to the lambda function based on your use\-case\.

```
import boto3
import email
import os

def email_handler(event, context):
    workmail = boto3.client('workmailmessageflow', region_name=os.environ["AWS_REGION"])
    msg_id = event['messageId']
    raw_msg = workmail.get_raw_message_content(messageId=msg_id)

    parsed_msg = email.message_from_bytes(raw_msg['messageContent'].read())
    print(parsed_msg)
```

For more detailed examples of ways to analyze the content of messages that are in transit, see the [amazon\-workmail\-lambda\-templates](https://github.com/aws-samples/amazon-workmail-lambda-templates) repository on GitHub\.

**Note**  
You only use the Amazon WorkMail Message Flow API to access email messages in transit\. You can only access the messages within 24 hours of being sent or received\. To programmatically access messages in a user’s mailbox, use one of the other protocols supported by Amazon WorkMail, such as IMAP or Exchange Web Services \(EWS\)\.