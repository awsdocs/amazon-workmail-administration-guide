# Prerequisites<a name="prereqs"></a>

To act as an Amazon WorkMail administrator, you need an AWS account\. If you haven't signed up for AWS yet, complete the following tasks to get set up\.

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

The AWS Management Console requires your username and password so that the service can determine whether you have permission to access its resources\. As a best practice, use AWS Identity and Access Management \(IAM\) to create an IAM user, and then add that user to an IAM group with administrative permissions\. You can then access the console using the credentials for the IAM user\. For more information, see [Creating your first IAM admin user and user group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) in the *IAM User Guide*\.

**Important**  
We don't recommend using root account credentials to access AWS because those credentials can't be revoked or limited in any way\.

### Grant IAM users permissions for Amazon WorkMail<a name="iam_policies_workmail"></a>

By default, IAM users don't have permissions to manage Amazon WorkMail resources\. You must attach an AWS managed policy \(**AmazonWorkMailFullAccess** or **AmazonWorkMailReadOnlyAccess**\) or create a customer\-managed policy that explicitly grants IAM users those permissions\. You then attach the policy to the IAM users or groups that require those permissions\. For more information, see [Identity and access management for Amazon WorkMail](security-iam.md)\.