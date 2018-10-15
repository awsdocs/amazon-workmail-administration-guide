# Prerequisites<a name="prereqs"></a>

To use Amazon WorkMail you'll need an AWS account\. If you haven't signed up for AWS yet, complete the following tasks to get set up\.

**Topics**
+ [Get an AWS Account and Your AWS account root user Credentials](#getting-started-signup)
+ [Create AWS Identity and Access Management Users and Groups](#iam_users_groups)

## Get an AWS Account and Your AWS account root user Credentials<a name="getting-started-signup"></a>

To access AWS, you must sign up for an AWS account\.

**To sign up for an AWS account**

1. Open [https://aws\.amazon\.com/](https://aws.amazon.com/), and then choose **Create an AWS Account**\.
**Note**  
If you previously signed in to the AWS Management Console using AWS account root user credentials, choose **Sign in to a different account**\. If you previously signed in to the console using IAM credentials, choose **Sign\-in using root account credentials**\. Then choose **Create a new AWS account**\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code using the phone keypad\.

 AWS sends you a confirmation e\-mail after the sign\-up process is complete\. At any time, you can view your current account activity and manage your account by going to [https://aws\.amazon\.com/](https://aws.amazon.com/) and choosing **My Account**\.

**To get the access key ID and secret access key for an IAM user**

Access keys consist of an access key ID and secret access key, which are used to sign programmatic requests that you make to AWS\. If you don't have access keys, you can create them from the AWS Management Console\. We recommend that you use IAM access keys instead of AWS account root user access keys\. IAM lets you securely control access to AWS services and resources in your AWS account\.

The only time that you can view or download the secret access keys is when you create the keys\. You cannot recover them later\. However, you can create new access keys at any time\. You must also have permissions to perform the required IAM actions\. For more information, see [Permissions Required to Access IAM Resources](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions-required.html) in the *IAM User Guide*\.

1. Open the [IAM console](https://console.aws.amazon.com/iam/home?#home)\.

1. In the navigation pane of the console, choose **Users**\.

1. Choose your IAM user name \(not the check box\)\.

1. Choose the **Security credentials** tab and then choose **Create access key**\.

1. To see the new access key, choose **Show**\. Your credentials will look something like this:
   + Access key ID: AKIAIOSFODNN7EXAMPLE
   + Secret access key: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

1. To download the key pair, choose **Download \.csv file**\. Store the keys in a secure location\.

   Keep the keys confidential in order to protect your AWS account, and never email them\. Do not share them outside your organization, even if an inquiry appears to come from AWS or Amazon\.com\. No one who legitimately represents Amazon will ever ask you for your secret key\.

**Related topics**
+ [What Is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) in the *IAM User Guide*
+ [AWS Security Credentials](https://docs.aws.amazon.com/general/latest/gr/aws-security-credentials.html) in *AWS General Reference* 

## Create AWS Identity and Access Management Users and Groups<a name="iam_users_groups"></a>

The AWS Management Console requires your username and password so that the service can determine whether you have permission to access its resources\. We recommend that you avoid using root account credentials to access AWS because root account credentials cannot be revoked or limited in any way\. Instead, use AWS Identity and Access Management \(IAM\) to create an IAM user and add the user to an IAM group with administrative permissions\. You can then access the console using the credentials for the IAM user\.

If you signed up for AWS but have not created an IAM user for yourself, you can create one using the IAM console\. For more information, see [Create Individual IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPractices.html#create-iam-users) in *IAM User Guide*\.

### Grant IAM Users Permissions for Amazon WorkMail<a name="iam_policies_workmail"></a>

By default, IAM users don't have permissions to manage Amazon WorkMail resources; you must attach an AWS managed policy \(**AmazonWorkMailFullAccess** or **AmazonWorkMailReadOnlyAccess**\) or create a customer managed policy that explicitly grants IAM users those permissions, and attach the policy to the specific IAM users or groups that require those permissions\. For more information, see [Managing Managed Policies Using the AWS Management Console](https://docs.aws.amazon.com/IAM/latest/UserGuide/managing-managed-policies-console.html) in *IAM User Guide*\. For more information, see [Permissions and Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/PermissionsAndPolicies.html) in *IAM User Guide*\.

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