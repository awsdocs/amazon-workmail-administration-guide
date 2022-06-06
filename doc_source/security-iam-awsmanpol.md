# AWS managed policies for Amazon WorkMail<a name="security-iam-awsmanpol"></a>

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the **ReadOnlyAccess** AWS managed policy provides read\-only access to all AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

## AWS managed policy: AmazonWorkMailFullAccess<a name="security-iam-awsmanpol-AmazonWorkMailFullAccess"></a>

You can attach the `AmazonWorkMailFullAccess` policy to your IAM identities\. This policy grants permissions that allow full access to Amazon WorkMail\.

To view the permissions for this policy, see [AmazonWorkMailFullAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AmazonWorkMailFullAccess) in the AWS Management Console\.

## AWS managed policy: AmazonWorkMailReadOnlyAccess<a name="security-iam-awsmanpol-AmazonWorkMailReadOnlyAccess"></a>

You can attach the `AmazonWorkMailReadOnlyAccess` policy to your IAM identities\. This policy grants permissions that allow read\-only access to Amazon WorkMail\.

To view the permissions for this policy, see [AmazonWorkMailReadOnlyAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AmazonWorkMailReadOnlyAccess) in the AWS Management Console\.

## AWS managed policy: AmazonWorkMailEventsServiceRolePolicy<a name="security-iam-awsmanpol-AmazonWorkMailEventsServiceRolePolicy"></a>

This policy is attached to the service\-linked role named **AmazonWorkMailEvents** to allow access to AWS services and resources used or managed by Amazon WorkMail events\. For more information, see [Using service\-linked roles for Amazon WorkMail](using-service-linked-roles.md)\.

## Amazon WorkMail updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>

View details about updates to AWS managed policies for Amazon WorkMail since this service began tracking these changes\.


| Change | Description | Date | 
| --- | --- | --- | 
|  Amazon WorkMail started tracking changes  |  Amazon WorkMail started tracking changes for its AWS managed policies\.  | March 1, 2021 | 