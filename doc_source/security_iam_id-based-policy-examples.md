# Amazon WorkMail identity\-based policy examples<a name="security_iam_id-based-policy-examples"></a>

By default, IAM users and roles don't have permission to create or modify Amazon WorkMail resources\. They also can't perform tasks using the AWS Management Console, AWS CLI, or AWS API\. An IAM administrator must create IAM policies that grant users and roles permission to perform specific API operations on the specified resources they need\. The administrator must then attach those policies to the IAM users or groups that require those permissions\.

To learn how to create an IAM identity\-based policy using these example JSON policy documents, see [Creating policies on the JSON tab](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

**Topics**
+ [Policy best practices](#security_iam_service-with-iam-policy-best-practices)
+ [Using the Amazon WorkMail console](#security_iam_id-based-policy-examples-console)
+ [Allow users to view their own permissions](#security_iam_id-based-policy-examples-view-own-permissions)
+ [Allow users read\-only access to Amazon WorkMail resources](#security_iam_id-based-policy-examples-read-only-access)

## Policy best practices<a name="security_iam_service-with-iam-policy-best-practices"></a>

Identity\-based policies determine whether someone can create, access, or delete Amazon WorkMail resources in your account\. These actions can incur costs for your AWS account\. When you create or edit identity\-based policies, follow these guidelines and recommendations:
+ **Get started with AWS managed policies and move toward least\-privilege permissions** – To get started granting permissions to your users and workloads, use the *AWS managed policies* that grant permissions for many common use cases\. They are available in your AWS account\. We recommend that you reduce permissions further by defining AWS customer managed policies that are specific to your use cases\. For more information, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) or [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.
+ **Apply least\-privilege permissions** – When you set permissions with IAM policies, grant only the permissions required to perform a task\. You do this by defining the actions that can be taken on specific resources under specific conditions, also known as *least\-privilege permissions*\. For more information about using IAM to apply permissions, see [ Policies and permissions in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) in the *IAM User Guide*\.
+ **Use conditions in IAM policies to further restrict access** – You can add a condition to your policies to limit access to actions and resources\. For example, you can write a policy condition to specify that all requests must be sent using SSL\. You can also use conditions to grant access to service actions if they are used through a specific AWS service, such as AWS CloudFormation\. For more information, see [ IAM JSON policy elements: Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) in the *IAM User Guide*\.
+ **Use IAM Access Analyzer to validate your IAM policies to ensure secure and functional permissions** – IAM Access Analyzer validates new and existing policies so that the policies adhere to the IAM policy language \(JSON\) and IAM best practices\. IAM Access Analyzer provides more than 100 policy checks and actionable recommendations to help you author secure and functional policies\. For more information, see [IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html) in the *IAM User Guide*\.
+ **Require multi\-factor authentication \(MFA\)** – If you have a scenario that requires IAM users or a root user in your AWS account, turn on MFA for additional security\. To require MFA when API operations are called, add MFA conditions to your policies\. For more information, see [ Configuring MFA\-protected API access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_configure-api-require.html) in the *IAM User Guide*\.

For more information about best practices in IAM, see [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) in the *IAM User Guide*\.

## Using the Amazon WorkMail console<a name="security_iam_id-based-policy-examples-console"></a>

To access the Amazon WorkMail console, you must have a minimum set of permissions\. These permissions must allow you to list and view details about the Amazon WorkMail resources in your AWS account\. If you create an identity\-based policy that is more restrictive than the minimum required permissions, the console won't function as intended for entities \(IAM users or roles\) with that policy\.

To ensure that those entities can still use the Amazon WorkMail console, also attach the following AWS managed policy, **AmazonWorkMailFullAccess**, to the entities\. For more information, see [Adding permissions to a user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html#users_change_permissions-add-console) in the *IAM User Guide*\.

The **AmazonWorkMailFullAccess** policy grants an IAM user full access to Amazon WorkMail resources\. This policy gives the user access to all Amazon WorkMail, AWS Key Management Service, Amazon Simple Email Service, and AWS Directory Service operations\. This also includes several Amazon EC2 operations that Amazon WorkMail needs to perform on your behalf\. The `logs` and `cloudwatch` permissions are required for email event logging and viewing metrics in the Amazon WorkMail console\. For more information, see [Logging and monitoring in Amazon WorkMail](monitoring-overview.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ds:AuthorizeApplication",
                "ds:CheckAlias",
                "ds:CreateAlias",
                "ds:CreateDirectory",
                "ds:CreateIdentityPoolDirectory",
                "ds:DeleteAlias",
                "ds:DeleteDirectory",
                "ds:DescribeDirectories",
                "ds:GetDirectoryLimits",
                "ds:ListAuthorizedApplications",
                "ds:UnauthorizeApplication",
                "ec2:AuthorizeSecurityGroupEgress",
                "ec2:AuthorizeSecurityGroupIngress",
                "ec2:CreateNetworkInterface",
                "ec2:CreateSecurityGroup",
                "ec2:CreateSubnet",
                "ec2:CreateTags",
                "ec2:CreateVpc",
                "ec2:DeleteSecurityGroup",
                "ec2:DeleteSubnet",
                "ec2:DeleteVpc",
                "ec2:DescribeAvailabilityZones",
                "ec2:DescribeRouteTables",
                "ec2:DescribeSubnets",
                "ec2:DescribeVpcs",
                "ec2:RevokeSecurityGroupEgress",
                "ec2:RevokeSecurityGroupIngress",
                "kms:DescribeKey",
                "kms:ListAliases"
                "lambda:ListFunctions",
                "route53:ChangeResourceRecordSets",
                "route53:ListHostedZones",
                "route53:ListResourceRecordSets",
                "route53domains:CheckDomainAvailability",
                "route53domains:ListDomains",
                "ses:*",
                "workmail:*",
                "iam:ListRoles",
                "logs:DescribeLogGroups",
                "logs:CreateLogGroup",
                "logs:PutRetentionPolicy",
                "cloudwatch:GetMetricData"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "iam:CreateServiceLinkedRole",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "iam:AWSServiceName": "events.workmail.amazonaws.com"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "iam:DeleteServiceLinkedRole",
                "iam:GetServiceLinkedRoleDeletionStatus"
            ],
            "Resource": "arn:aws:iam::*:role/aws-service-role/events.workmail.amazonaws.com/AWSServiceRoleForAmazonWorkMailEvents*"
        },
        {
            "Effect": "Allow",
            "Action": "iam:PassRole",
            "Resource": "arn:aws:iam::*:role/*workmail*",
            "Condition": {
                "StringLike": {
                    "iam:PassedToService": "events.workmail.amazonaws.com"
                }
            }
        }
    ]
}
```

You don't need to allow minimum console permissions for users that are making calls only to the AWS CLI or the AWS API\. Instead, allow access to only the actions that match the API operation that you're trying to perform\.

## Allow users to view their own permissions<a name="security_iam_id-based-policy-examples-view-own-permissions"></a>

This example shows how you might create a policy that allows IAM users to view the inline and managed policies that are attached to their user identity\. This policy includes permissions to complete this action on the console or programmatically using the AWS CLI or AWS API\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ViewOwnUserInfo",
            "Effect": "Allow",
            "Action": [
                "iam:GetUserPolicy",
                "iam:ListGroupsForUser",
                "iam:ListAttachedUserPolicies",
                "iam:ListUserPolicies",
                "iam:GetUser"
            ],
            "Resource": ["arn:aws:iam::*:user/${aws:username}"]
        },
        {
            "Sid": "NavigateInConsole",
            "Effect": "Allow",
            "Action": [
                "iam:GetGroupPolicy",
                "iam:GetPolicyVersion",
                "iam:GetPolicy",
                "iam:ListAttachedGroupPolicies",
                "iam:ListGroupPolicies",
                "iam:ListPolicyVersions",
                "iam:ListPolicies",
                "iam:ListUsers"
            ],
            "Resource": "*"
        }
    ]
}
```

## Allow users read\-only access to Amazon WorkMail resources<a name="security_iam_id-based-policy-examples-read-only-access"></a>

The following policy statement grants an IAM user read\-only access to Amazon WorkMail resources\. This policy gives the same level of access as the AWS managed policy **AmazonWorkMailReadOnlyAccess**\. Either policy gives the user access to all of the Amazon WorkMail `Describe` operations\. Access to the AWS Directory Service `DescribeDirectories` operation is needed to obtain information about your AWS Directory Service directories\. Access to the Amazon SES service is needed to obtain information about the configured domains\. Access to AWS Key Management Service is needed to obtain information about the used encryption keys\. The `logs` and `cloudwatch` permissions are required for email event logging and viewing metrics in the Amazon WorkMail console\. For more information, see [Logging and monitoring in Amazon WorkMail](monitoring-overview.md)\.

```
{
        "Version": "2012-10-17",
        "Statement": [
                        {
                         "Effect": "Allow",
                         "Action": [
                                    "ses:Describe*",
                                    "ses:Get*",
                                    "workmail:Describe*",
                                    "workmail:Get*",
                                    "workmail:List*",
                                    "workmail:Search*",
                                    "lambda:ListFunctions",
                                    "iam:ListRoles",
                                    "logs:DescribeLogGroups",
                                    "cloudwatch:GetMetricData"
                                   ],
                         "Resource": "*"
                        }
                  ]
  }
}
```