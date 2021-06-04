# Updating message content with AWS Lambda<a name="update-with-lambda"></a>

After you configure a synchronous AWS Lambda function to manage email flows, you can use the `PutRawMessageContent` action in the Amazon WorkMail Message flow API to update the content of in\-transit email messages\. For more information about getting started with Lambda functions for Amazon WorkMail, see [Configuring synchronous **Run Lambda** rules](lambda.md#synchronous-rules)\. For more information about the API, see [ PutRawMessageContent](https://docs.aws.amazon.com/workmail/latest/APIReference/API_messageflow_PutRawMessageContent.html)\.

**Note**  
The PutRawMessageContent API requires boto3 1\.17\.8, or you can add a layer to your Lambda function\. To download the correct boto3 version, see the [boto page on GitHub](https://github.com/boto/boto)\. For more information about adding layers, see [Configure a function to use layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html#configuration-layers-using)\.   
Here's an example layer: `Layer Name: “arn:aws:lambda:${AWS::Region}:489970191081:layer:WorkMailLambdaLayer:2”`\. In this example, substitute `${AWS::Region}` with an appropriate aws region such as us\-east\-1\.

**Tip**  
If you start by deploying the Amazon WorkMail [Hello World Lambda function](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:489970191081:applications/workmail-hello-world-python) from the AWS Serverless Application Repository to your account, the system creates a Lambda function in your account with the necessary resources and permissions\. You can then add business logic to the lambda function, based on your use cases\.

As you go, remember the following:
+ Use the [ GetRawMessageContent](https://docs.aws.amazon.com/workmail/latest/APIReference/API_messageflow_GetRawMessageContent.html) API to retrieve the original message content\. For more information see [Retrieving message content with AWS Lambda](lambda-content.md)\.
+ Once you have the original message, change the MIME content\. When you finish, upload the message to an S3 bucket in your account\. Ensure that the S3 bucket uses the same AWS account as your Amazon WorkMail operations, and that it uses the same AWS Region as your API calls\.
+ For Amazon WorkMail to process requests, your S3 bucket must have the correct policy in order to access the S3 object\. For more information, see [Example S3 policy](#s3example)\.
+ Use the [ PutRawMessageContent](https://docs.aws.amazon.com/workmail/latest/APIReference/API_messageflow_PutRawMessageContent.html) API to send the updated the message content back to Amazon WorkMail\.

**Note**  
The `PutRawMessageContent` API ensures that the MIME content of the updated message meets RFC standards, as wells as the criteria mentioned in the [RawMessageContent](https://docs.aws.amazon.com/workmail/latest/APIReference/API_messageflow_RawMessageContent.html) data type\. Emails inbound to your Amazon WorkMail organization do not always meet those standards, so the `PutRawMessageContent` API may reject them\. In such cases, you can consult the error message returned for more information on how to fix any issues\.

**Example S3 policy**  

```
{
    "Version": "2008-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "workmail.region.amazonaws.com"
            },
            "Action": [
                "s3:GetObject",
                "s3:GetObjectVersion"
            ],
            "Resource": "arn:aws:s3:::My-Test-S3-Bucket/*",
            "Condition": {
                "Bool": {
                    "aws:SecureTransport": "true"
                }
            }
        }
    ]
}
```

The following example shows how a Lambda function uses the Python runtime to update the subject of an in\-transit email message\.

```
    import boto3
    import os
    import uuid
    import email
     
    def email_handler(event, context):
        workmail = boto3.client('workmailmessageflow', region_name=os.environ["AWS_REGION"])
        s3 = boto3.client('s3', region_name=os.environ["AWS_REGION"])
        
        msg_id = event['messageId']
        raw_msg = workmail.get_raw_message_content(messageId=msg_id)
        parsed_msg = email.message_from_bytes(raw_msg['messageContent'].read())
        
        # Updating subject. For more examples, see https://github.com/aws-samples/amazon-workmail-lambda-templates.
        parsed_msg.replace_header('Subject', "New Subject Updated From Lambda")
       
        # Store updated email in S3
        key = str(uuid.uuid4());
        s3.put_object(Body=parsed_msg.as_bytes(), Bucket="Your-S3-Bucket", Key=key)
     
        # Update the email in WorkMail
        s3_reference = {
            'bucket': "Your-S3-Bucket",
            'key': key
        }
        content = {
            's3Reference': s3_reference
        }
        workmail.put_raw_message_content(messageId=msg_id, content=content)
```

For more examples of ways to analyze the content of in\-transit messages, see the [ amazon\-workmail\-lambda\-templates ](https://github.com/aws-samples/amazon-workmail-lambda-templates) repository on GitHub\.