# Integrate Amazon WorkMail with an Existing Directory \(Standard Setup\)<a name="premises_directory"></a>

You can integrate Amazon WorkMail with an existing directory such as an on\-premises Microsoft Active Directory, AWS Managed Active Directory, or AWS Simple Active Directory\. By integrating with your on\-premises directory, you can reuse your existing users and groups in Amazon WorkMail and users can log in with their existing credentials\.

You also have the option to select a specific master key that Amazon WorkMail uses to encrypt the mailbox content\. You can either select the default master key for Amazon WorkMail or create a custom master key in AWS KMS to use with Amazon WorkMail\. 

If the existing directory is on\-premises, you must first set up an AD Connector in AWS Directory Service\. The AD Connector is used to synchronize your users and groups to the Amazon WorkMail address book and perform user authentication requests\.

For information about setting up an AD Connector, see [Connecting to Your Existing Directory with AD Connector](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/create_directory.html#connect_directory) in the *AWS Directory Service Administration Guide*\.

**To perform a Standard setup**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. In the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. Choose **Get started**\.

1. On the **Set up your organization** screen, choose **Standard setup**\.

1. On the **Standard setup** screen, for **Available Directories**, select your existing directory\.
**Note**  
If you have an on\-premises Active Directory with Microsoft Exchange and an AWS AD Connector, choose **Enable interoperability** on the **Interoperability with Microsoft Exchange** screen\. Interoperability allows you to minimize disruption to your users as you migrate mailboxes to Amazon WorkMail, or use Amazon WorkMail for a subset of your corporate mailboxes\. For more information, see [Interoperability between Amazon WorkMail and Microsoft Exchange](http://docs.aws.amazon.com/workmail/latest/adminguide/interoperability.html)\. 

1. For **Master keys**, select a master key\. You can either select the default master key or create a custom master key in AWS Key Management Service\.
**Note**  
For information about creating a new master key, see [Creating Keys](http://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.  
If you are logged on as an IAM user, make yourself a key administrator on the master key\. For more information, see [Enabling and Disabling Keys](http://docs.aws.amazon.com/kms/latest/developerguide/enabling-keys.html) in the *AWS Key Management Service Developer Guide*\.