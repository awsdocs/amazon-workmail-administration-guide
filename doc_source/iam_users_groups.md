# AWS Identity and Access Management Users and Groups<a name="iam_users_groups"></a>

The AWS Management Console requires your username and password so that the service can determine whether you have permission to access its resources\. We recommend that you avoid using root account credentials to access AWS because root account credentials cannot be revoked or limited in any way\. Instead, use AWS Identity and Access Management \(IAM\) to create an IAM user and add the user to an IAM group with administrative permissions\. You can then access the console using the credentials for the IAM user\.

If you signed up for AWS but have not created an IAM user for yourself, you can create one using the IAM console\. For more information, see [Create Individual IAM Users](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPractices.html#create-iam-users) in *IAM User Guide*\.

## AWS Identity and Access Management Policies for Amazon WorkMail<a name="iam_policies_workmail"></a>

By default, IAM users don't have permissions to manage Amazon WorkMail resources; you must attach an AWS managed policy \(**AmazonWorkMailFullAccess** or **AmazonWorkMailReadOnlyAccess**\) or create a customer managed policy that explicitly grants IAM users those permissions, and attach the policy to the specific IAM users or groups that require those permissions\. For more information, see [Managing Managed Policies Using the AWS Management Console](http://docs.aws.amazon.com/IAM/latest/UserGuide/managing-managed-policies-console.html) in *IAM User Guide*\. For more information, see [Permissions and Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/PermissionsAndPolicies.html) in *IAM User Guide*\.

The following customer managed policy statement grants an IAM user full access to Amazon WorkMail resources\. This customer managed policy gives the same level of access as the AWS managed policy **AmazonWorkMailFullAccess**\. Either policy gives the user access to all Amazon WorkMail, AWS Key Management Service, Amazon Simple Email Service, and AWS Directory Service operations, as well as several Amazon EC2 operations that Amazon WorkMail needs to be able to perform on your behalf\.

```
"amazonWorkMailFullAccess": {
  "name": "Amazon WorkMail Full Access",
  "description": "Provides full access to WorkMail, Directory Service, SES, EC2 and read access to KMS metadata.",
  "policyDocument": {
        "Version": "2012-10-17",
        "Statement": [
                        {
                          "Effect": "Allow",
                          "Action": [
                                     "workmail:*",
                                     "ds:AuthorizeApplication",
                                     "ds:CheckAlias",
                                     "ds:CreateAlias",
                                     "ds:CreateDirectory",
                                     "ds:CreateDomain",
                                     "ds:DeleteAlias",
                                     "ds:DeleteDirectory",
                                     "ds:DescribeDirectories",
                                     "ds:ExtendDirectory",
                                     "ds:GetDirectoryLimits",
                                     "ds:ListAuthorizedApplications",
                                     "ds:UnauthorizeApplication",
                                     "ses:*",
                                     "ec2:AuthorizeSecurityGroupEgress",
                                     "ec2:AuthorizeSecurityGroupIngress",
                                     "ec2:CreateNetworkInterface",
                                     "ec2:CreateSecurityGroup",
                                     "ec2:DeleteSecurityGroup",
                                     "ec2:CreateSubnet",
                                     "ec2:DeleteSubnet",
                                     "ec2:CreateVpc",
                                     "ec2:DeleteVpc",
                                     "ec2:DescribeRouteTables",
                                     "ec2:DescribeSubnets",
                                     "ec2:DescribeVpcs",
                                     "ec2:DescribeAvailabilityZones",
                                     "ec2:CreateTags",
                                     "ec2:RevokeSecurityGroupEgress",
                                     "ec2:RevokeSecurityGroupIngress",
                                     "kms:DescribeKey",
                                     "kms:ListAliases"
                                     ],
                         "Resource": "*"
                       }
                  ]
  }
}
```

The following customer managed policy statement grants an IAM user read\-only access to Amazon WorkMail resources\. This customer managed policy gives the same level of access as the AWS managed policy **AmazonWorkMailReadOnlyAccess**\. Either policy gives the user access to all of the Amazon WorkMail Describe operations\. Access to the two Amazon EC2 operations are necessary so Amazon WorkMail can obtain a list of your VPCs and subnets\. Access to the AWS Directory Service `DescribeDirectories` operation is needed to obtain information about your AWS Directory Service directories\. Access to the Amazon SES service is needed to obtain information about the configured domains and access to AWS Key Management Service is needed to obtain information about the used encryption keys\.

```
"amazonWorkMailROAccess": {
  "name": "Amazon WorkMail Read Only Access",
  "description": "Provides read only access to WorkMail and SES.",
  "policyDocument": {
        "Version": "2012-10-17",
        "Statement": [
                        {
                         "Effect": "Allow",
                         "Action": [
                                    "workmail:Get*",
                                    "workmail:List*",
                                    "workmail:Describe*",
                                    "workmail:Search*",
                                    "ses:Get*",
                                    "ses:Describe*"
                                   ],
                         "Resource": "*"
                        }
                  ]
  }
}
```