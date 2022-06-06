# Getting started with Amazon WorkMail<a name="howto-start"></a>

Whether you're a new Amazon WorkMail user or an existing user of Amazon WorkDocs or Amazon WorkSpaces, get started with Amazon WorkMail by completing the following steps\.

**Note**  
Complete the [Prerequisites](prereqs.md) before getting started\.

**Topics**
+ [Step 1: Sign in to the Amazon WorkMail console](#workmail_signin)
+ [Step 2: Set up your Amazon WorkMail site](#setup-site)
+ [Step 3: Set up Amazon WorkMail user access](#setup-user)
+ [More resources](#more-getting-started)

## Step 1: Sign in to the Amazon WorkMail console<a name="workmail_signin"></a>

You must sign in to the Amazon WorkMail console before you can add users and manage their accounts and mailboxes\.

**To sign in to the Amazon WorkMail console**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information about regions, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

## Step 2: Set up your Amazon WorkMail site<a name="setup-site"></a>

1. After you sign in to the Amazon WorkMail console, you set up your organization and add a domain\. We recommend using a dedicated domain for your Amazon WorkMail organization\. For more information, see [Creating an organization](add_new_organization.md) and [Adding a domain](add_domain.md)\.

1. \(Optional\) You can choose to use a free testing domain provided by Amazon WorkMail\. If you choose to do this, skip to step 4\.
**Note**  
Test domains use this format: *alias*\.awsapps\.com\. As you go, remember that you should only use test domains for testing\. Don't use a test domain for a production environment\. Also, you must have at least one enabled user in your Amazon WorkMail organization\. If you don't have an enabled user, the domain can become available for registration and use by other customers\.

1. If you use an external domain, verify that domain by adding the appropriate text \(TXT\) and mail exchange \(MX\) records to your Domain Name System \(DNS\) service\. TXT records allow you to enter notes in the DNS\. MX records specify the incoming mail servers\. Make sure to set your domain as the default for your organization\. For more information, see [Verifying domains](domain_verification.md) and [Choosing the default domain](default_domain.md)\.

1. Create new users or enable your existing directory users for Amazon WorkMail\. For more information, see [Managing user accounts](manage-users.md)\.

1. \(Optional\) If you have existing Microsoft Exchange mailboxes, migrate them to Amazon WorkMail\. For more information, see [Migrating to Amazon WorkMail](migration_overview.md)\.

After you've finished setting up your Amazon WorkMail site, you can access Amazon WorkMail using the web application URL\.

**To locate your Amazon WorkMail web application URL**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. To do so, open the **Select a region** list, located to the right of the search box, then choose the desired Region\. For more information, see [Region and endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of your organization\.

   The **Organization settings** page appears and displays the URL under **User login**\. The URLs take this form: https://*alias*\.awsapps\.com/mail\.

## Step 3: Set up Amazon WorkMail user access<a name="setup-user"></a>

Choose from the following options to set up Amazon WorkMail user access:
+ Set up user access from an existing desktop client using the Microsoft Outlook client\. For more information, see [Connect Microsoft Outlook to your Amazon WorkMail account](https://docs.aws.amazon.com/workmail/latest/userguide/connect_mail_client.html)\.
+ Set up user access from a mobile device, such as a Kindle, Android, iPad, or iPhone\. For more information, see [Getting started with a mobile device](https://docs.aws.amazon.com/workmail/latest/userguide/mobile-start.html)\.
+ To set up user access, use any client software compatible with the Internet Mail Access Protocol \(IMAP\) protocol\. For more information, see [Connect IMAP clients to Your Amazon WorkMail account](https://docs.aws.amazon.com/workmail/latest/userguide/using_IMAP_client.html)\.

## More resources<a name="more-getting-started"></a>
+ [Migrating to Amazon WorkMail](migration_overview.md)
+ [Interoperability between Amazon WorkMail and Microsoft Exchange](interoperability.md)
+ [Amazon WorkMail quotas](workmail_limits.md)