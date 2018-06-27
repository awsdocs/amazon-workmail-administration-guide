# Set up Amazon WorkMail with Quick Setup<a name="quick_setup"></a>

You can use the **Quick setup** option to create an Amazon WorkMail organization\. Amazon WorkMail does the following for you:
+ Creates a new WorkMail Directory for storing your users and groups\. You cannot view this type of directory in AWS Directory Service\.
+ Creates a free test domain\.
+ Uses the default KMS master key for encrypting your mailbox contents\.

**Note**  
Directories created using the Amazon WorkMail **Quick setup** option do not support nested groups, and they are not compatible with Amazon WorkDocs or Amazon WorkSpaces\. For more information about creating a compatible directory, see [Set up Amazon WorkMail using Amazon WorkDocs or Amazon WorkSpaces](#compatible)\.

**To add an organization using the Quick setup option**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. In the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. Choose **Get started**\.

1. On the **Set up your organization** screen, choose **Quick setup**\.

1. On the **Quick setup** screen, for **Organization name**, enter a unique alias to be used as your mail domain, and then choose **Create**\.

   After your organization is created, you can add domains, users, and groups\.
**Note**  
If you exceed the number of organizations you can create using the Quick setup, you receive the error 'You have reached the maximum number of organizations you can create'\. For more information, see [Amazon WorkMail Limits](what_is.md#workmail_limits)\.

## Set up Amazon WorkMail using Amazon WorkDocs or Amazon WorkSpaces<a name="compatible"></a>

To use Amazon WorkMail with Amazon WorkDocs or Amazon WorkSpaces, create a compatible directory by following the steps below\.

**To add a compatible Amazon WorkDocs or Amazon WorkSpaces organization**

1. Create a compatible directory using Amazon WorkDocs or Amazon WorkSpaces\.

   1. For Amazon WorkDocs instructions, see [Creating a Simple AD Directory Using the Quick Start](http://docs.aws.amazon.com/workdocs/latest/adminguide//cloud_quick_start.html)\.

   1. For Amazon WorkSpaces instructions, see [Get Started with Amazon WorkSpaces Quick Setup](http://docs.aws.amazon.com/workspaces/latest/adminguide/getting-started.html)\.

1. From the Amazon WorkMail console, complete the Amazon WorkMail setup\. For more information, see [Integrate Amazon WorkMail with an Existing Directory \(Standard Setup\)](premises_directory.md)\.