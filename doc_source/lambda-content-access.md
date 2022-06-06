# Managing access to the Amazon WorkMail Message Flow API<a name="lambda-content-access"></a>

Use AWS Identity and Access Management \(IAM\) policies to manage access to the Amazon WorkMail Message Flow API\.

The Amazon WorkMail Message Flow API works with a single resource type, an email message in transit\. Each email message in transit has a unique Amazon Resource Name \(ARN\) associated with it\.

The following example shows the syntax of an ARN associated with an email message in transit\.

```
arn:aws:workmailmessageflow:region:account:message/organization/context/messageID
```

Changeable fields in the preceding example include the following:
+ **Region** – The AWS Region for your Amazon WorkMail organization\.
+ **Account** – The AWS account ID for your Amazon WorkMail organization\.
+ **Organization** – Your Amazon WorkMail organization ID\.
+ **Context** – Indicates whether the message is `incoming` to your organization, or `outgoing` from it\.
+ **Message ID** – The unique email message ID that is passed as input to your Lambda function\.

The following example includes example IDs for an ARN associated with an incoming email message in transit\.

```
arn:aws:workmailmessageflow:us-east-1:111122223333:message/m-n1pq2345678r901st2u3vx45x6789yza/incoming/d1234567-8e90-1f23-456g-hjk7lmnop8q9                
```

You can use these ARNs as resources in the `Resource` section of your IAM user policies in order to manage access to Amazon WorkMail messages in transit\. For more information about granting IAM users permissions for Amazon WorkMail, see [Create AWS Identity and Access Management users and groups](prereqs.md#iam_users_groups)\.

## Example IAM policies for Amazon WorkMail message flow access<a name="lambda-content-policies"></a>

The following example policy grants an IAM entity full read access to all inbound and outbound messages for every Amazon WorkMail organization in your AWS account\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "workmailmessageflow:GetRawMessageContent"
            ],
            "Resource": "arn:aws:workmailmessageflow:region:account:message/*",
            "Effect": "Allow"
        }
    ]
}
```

If you have multiple organizations in your AWS account, you can also limit access to one or more organizations\. This is useful if certain Lambda functions should only be used for certain organizations\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "workmailmessageflow:GetRawMessageContent"
            ],
            "Resource": "arn:aws:workmailmessageflow:region:account:message/organization/*",
            "Effect": "Allow"
        }
    ]
}
```

You can also choose to grant access to messages depending on whether they are `incoming` to your organization, or `outgoing` from it\. To do this, use the qualifier `incoming` or `outgoing` in the ARN\. 

The following example policy grants access only to messages that are incoming to your organization\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "workmailmessageflow:GetRawMessageContent"
            ],
            "Resource": "arn:aws:workmailmessageflow:region:account:message/organization/incoming/*",
            "Effect": "Allow"
        }
    ]
}
```

The following example policy grants an IAM entity full read and update access to all inbound and outbound messages for every Amazon WorkMail organization in your AWS accounts\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "workmailmessageflow:GetRawMessageContent",
                "workmailmessageflow:PutRawMessageContent"
            ],
            "Resource": "arn:aws:workmailmessageflow:region:account:message/*",
            "Effect": "Allow"
        }
    ]
}
```