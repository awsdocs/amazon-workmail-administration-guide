# Creating an organization<a name="add_new_organization"></a>

To use Amazon WorkMail, you must first create an organization\. One AWS account can have multiple Amazon WorkMail organizations\. When you create an organization, you also select a domain for the organization and set up user directory and encryption settings\.

You can create a new user directory, or integrate Amazon WorkMail with an existing directory\. You can use Amazon WorkMail with an on\-premises Microsoft Active Directory, AWS Managed Active Directory, or Simple AD\. By integrating with your on\-premises directory, you can use your existing users and groups in Amazon WorkMail and users can sign in with their existing credentials\. If you’re using an on\-premises directory, you must first set up an AD Connector in AWS Directory Service\. The AD Connector synchronizes your users and groups with the Amazon WorkMail address book and performs user authentication requests\. For more information, see [Active Directory Connector](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/directory_ad_connector.html) in the *AWS Directory Service Administration Guide*\.

You also have the option of selecting a  AWS KMS key that Amazon WorkMail uses to encrypt the mailbox content\. You can either select the default AWS managed master key for Amazon WorkMail, or use an existing KMS key in AWS Key Management Service \(AWS KMS\)\. For information about creating a new KMS key, see [Creating keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\. If you are signed in as an AWS Identity and Access Management \(IAM\) user, make yourself a key administrator on the KMS key\. For more information, see [Enabling and disabling keys](https://docs.aws.amazon.com/kms/latest/developerguide/enabling-keys.html) in the *AWS Key Management Service Developer Guide*\.

**Considerations**  
Remember the following when creating an Amazon WorkMail organization:
+ Amazon WorkMail doesn't currently support managed Microsoft Active Directory services that you share with multiple accounts\.
+ If you have an on\-premises Active Directory with Microsoft Exchange and an AD Connector, we recommend configuring interoperability settings for your organization\. This allows you to minimize disruption to your users as you migrate mailboxes to Amazon WorkMail, or use Amazon WorkMail for a subset of your corporate mailboxes\. For more information, see [Interoperability between Amazon WorkMail and Microsoft Exchange](interoperability.md)\. 
+ If you select the **Free test domain** option, you can start using your Amazon WorkMail organization with the provided test domain\. The test domain uses this format: *example*\.awsapps\.com\. You can use the test mail domain with Amazon WorkMail and other supported AWS services as long as you maintain enabled users in your Amazon WorkMail organization\. However, you can't use the test domain for other purposes\. The test domain might become available for registration and use by other customers if your Amazon WorkMail organization does not maintain at least one enabled user\.
+ Amazon WorkMail does not support multi\-Region directories\.

**Topics**
+ [Creating an organization](#create-organization)
+ [Viewing an organization's details](#view-org-details)
+ [Integrating an Amazon WorkDocs or WorkSpaces directory](#compatible)
+ [Organization states and descriptions](#org-states)

## Creating an organization<a name="create-organization"></a>

Create a new organization in the Amazon WorkMail console\.

**To create an organization**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Region and endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation bar, select **Organization**\.

   The **Organizations** page appears and displays your organizations, if any\.

1. Choose **Create organization**\.

1. Under **Email domain**, select the domain to use for the email addresses in your organization:
   + ****Existing Route 53 domain**** – Select an existing domain that you manage with an Amazon Route 53 \(Route 53\) hosted zone\.
   + ****New Route 53 domain**** – Register a new Route 53 domain name to use with Amazon WorkMail\. 
   + ****External domain**** – Enter an existing domain that you manage with an external domain name system \(DNS\) provider\.
   + ****Free test domain**** – Use a free test domain provided by Amazon WorkMail\. You can explore Amazon WorkMail using a test domain, and then add a domain to your organization later\.

1. \(Optional\) If your domain is managed through Amazon Route 53, for **Route 53 hosted zone**, select your Route 53 domain\.

1. For **Alias**, enter a unique alias for your organization\.

1. Choose **Advanced settings**, and for **User directory**, select one of the following options:
   + **Create new Amazon WorkMail directory** – Creates a new directory for adding and managing your users\.
   + **Use existing directory** – Uses an existing directory to manage your users, such as an on\-premises Microsoft Active Directory, AWS Managed Active Directory, or Simple AD\.

1. For **Encryption**, select one of the following options:
   + **Use an Amazon WorkMail managed key** – Creates a new encryption key in your account\.
   + **Use existing KMS key** – Uses an existing KMS key that you have already created in AWS KMS\.

1. Choose **Create organization**\.

If you use an external domain, verify it by adding the appropriate text \(TXT\) and mail exchanger \(MX\) records to your DNS service\. TXT records allow you to enter notes about the DNS service\. MX records specify the incoming mail server\.

Be sure to set your domain as the default for your organization\. For more information, see [Verifying domains](domain_verification.md) and [Choosing the default domain](default_domain.md)\.

When your organization is **Active**, you can add users to it and set up their email clients\. For more information, see [Managing user accounts](manage-users.md) and [Setting up email clients for Amazon WorkMail](https://docs.aws.amazon.com/workmail/latest/userguide/clients.html)\.

## Viewing an organization's details<a name="view-org-details"></a>

Each of your Amazon WorkMail organizations can display an the organization details page\. The page shows you information about their organization, including IDs that you can use with the AWS Command Line Interface\. Messages on the page can also show you any steps needed to finish setting up and organization, such as an unverified domain or a lack of users\. The messages also provide the first step that you follow to set up a given email client\. 

**To view organization details**

1. In the navigation bar, choose **Organization**\.

   The **Organizations** page appears and displays your organizations\.

1. Choose the organization that you want to view\.

## Integrating an Amazon WorkDocs or WorkSpaces directory<a name="compatible"></a>

To use Amazon WorkMail with Amazon WorkDocs or WorkSpaces, create a compatible directory by using the following steps\.

**To add a compatible Amazon WorkDocs or WorkSpaces directory**

1. Create a compatible directory using Amazon WorkDocs or WorkSpaces\.

   1. For Amazon WorkDocs instructions, see [Getting started with Quick Start](https://docs.aws.amazon.com/workdocs/latest/adminguide/cloud_quick_start.html) in the *Amazon WorkDocs Administration Guide*\.

   1. For WorkSpaces instructions, see [Get started with Amazon WorkSpaces Quick Setup](https://docs.aws.amazon.com/workspaces/latest/adminguide/getting-started.html) in the *Amazon WorkSpaces Administration Guide*\.

1. In the Amazon WorkMail console, create your Amazon WorkMail organization and choose to use your existing directory for it\. For more information, see [Creating an organization](#create-organization)\.

## Organization states and descriptions<a name="org-states"></a>

After you create an organization, it can have one of the following states\.


****  

| **State** | Description | 
| --- | --- | 
|  **Active**  |  Your organization is healthy and ready for use\.  | 
|  **Creating**  |  A workflow is running to create your organization\.  | 
|  **Failed**  |  Your organization could not be created\.  | 
|  **Impaired**  |  Your organization is malfunctioning or an issue has been detected\.  | 
|  **Inactive**  |  Your organization is inactive\.  | 
|  **Requested**  |  Your organization creation request is in the queue and waiting to be created\.  | 
|  **Validating**  |  All settings for the organization are being health\-checked\.  | 