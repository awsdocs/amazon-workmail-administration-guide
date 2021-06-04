# Prerequisites<a name="prereqs"></a>

To use Amazon WorkMail you'll need an AWS account\. If you haven't signed up for AWS yet, complete the following tasks to get set up\.

**Topics**
+ [Get an AWS account and your root user credentials](#getting-started-signup)
+ [Create AWS Identity and Access Management users and groups](#iam_users_groups)

## Get an AWS account and your root user credentials<a name="getting-started-signup"></a>

To access AWS, you must sign up for an AWS account\.

**To sign up for an AWS account**

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

 AWS sends you a confirmation email after the sign\-up process is complete\. At any time, you can view your current account activity and manage your account by going to [https://aws\.amazon\.com/](https://aws.amazon.com/) and choosing **My Account**\.

## Create AWS Identity and Access Management users and groups<a name="iam_users_groups"></a>

The AWS Management Console requires your username and password so that the service can determine whether you have permission to access its resources\. We recommend that you avoid using root account credentials to access AWS because root account credentials cannot be revoked or limited in any way\. Instead, use AWS Identity and Access Management \(IAM\) to create an IAM user and add the user to an IAM group with administrative permissions\. You can then access the console using the credentials for the IAM user\.

If you signed up for AWS but have not created an IAM user for yourself, you can create one using the IAM console\. For more information, see [Create Individual IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPractices.html#create-iam-users) in *IAM User Guide*\.

### Grant IAM users permissions for Amazon WorkMail<a name="iam_policies_workmail"></a>

By default, IAM users don't have permissions to manage Amazon WorkMail resources; you must attach an AWS managed policy \(**AmazonWorkMailFullAccess** or **AmazonWorkMailReadOnlyAccess**\) or create a customer managed policy that explicitly grants IAM users those permissions, and attach the policy to the specific IAM users or groups that require those permissions\. For more information, see [Identity and access management for Amazon WorkMail](security-iam.md)\.