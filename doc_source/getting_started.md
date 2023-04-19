# Getting started with Amazon WorkMail<a name="getting_started"></a>

After you complete the [Prerequisites](prereqs.md), you're ready to get started with Amazon WorkMail\. For more information, see [Getting started with Amazon WorkMail](howto-start.md)\.

You can learn more about migrating existing mailboxes to Amazon WorkMail, interoperability with Microsoft Exchange, and Amazon WorkMail quotas in the following sections\.

**Topics**
+ [Getting started with Amazon WorkMail](howto-start.md)
+ [Migrating to Amazon WorkMail](migration_overview.md)
+ [Interoperability between Amazon WorkMail and Microsoft Exchange](interoperability.md)
+ [Configure availability settings on Amazon WorkMail](enable_interop_wm.md)
+ [Configure availability settings in Microsoft Exchange](enable_interop_ms.md)
+ [Enable email routing between Microsoft Exchange and Amazon WorkMail users](setup-msexchange.md)
+ [Enable email routing for a user](#enable_routing_user)
+ [Post setup configuration](#post_setup)
+ [Mail client configuration](#mail_client_config)
+ [Disabling interoperability mode and decommissioning your mail server](disable_interop.md)
+ [Troubleshooting](troubleshooting_interop.md)
+ [Amazon WorkMail quotas](workmail_limits.md)

## Enable email routing for a user<a name="enable_routing_user"></a>

We recommend that you complete the following steps first for test users before applying any changes to your organization\.

1. Enable the user account that you are migrating to Amazon WorkMail\. For more information, see [Enable existing users](https://docs.aws.amazon.com/workmail/latest/adminguide/enable_existing_user.html)\.

1. In the Amazon WorkMail console, ensure that there are at least two email addresses associated with the enabled user\. 
   + *workmailuser*@*orgname*\.awsapps\.com \(this is added automatically and can be used for tests without your Microsoft Exchange\.\)
   + *workmailuser*@*yourdomain*\.com \(this is added automatically and is the primary Microsoft Exchange address\.\)

     For more information, see [Edit user email addresses](https://docs.aws.amazon.com/workmail/latest/adminguide/edit_user_email_addresses.html)\.

1. Ensure that you migrate all data from the mailbox in Microsoft Exchange to the mailbox in Amazon WorkMail\. For more information, see [Migrating to Amazon WorkMail](https://docs.aws.amazon.com/workmail/latest/adminguide/migration_overview.html)\.

1. After all of the data is migrated, disable the mailbox for the user on Microsoft Exchange\. Then, create a mail user \(or mail\-enabled user\) that has the external SMTP address pointed to Amazon WorkMail\. To do this, use the following commands in the Exchange Management Shell:
**Important**  
The following steps erase the contents of the mailbox\. Ensure that your data has been migrated to Amazon WorkMail before you attempt to enable email routing\. Some mail clients don't seamlessly switch to Amazon WorkMail when you run this command\. For more information, see [Mail client configuration](#mail_client_config)\.

   ```
   $old_mailbox = Get-Mailbox exchangeuser
   ```

   ```
   Disable-Mailbox $old_mailbox
   ```

   ```
   $new_mailuser = Enable-MailUser $old_mailbox.Identity -ExternalEmailAddress workmailuser@orgname.awsapps.com -PrimarySmtpAddress $old_mailbox.PrimarySmtpAddress
   ```

   ```
   Set-MailUser $new_mailuser -EmailAddresses $old_mailbox.EmailAddresses -HiddenFromAddressListsEnabled $old_mailbox.HiddenFromAddressListsEnabled
   ```

   In the above commands, *orgname* represents the name of your Amazon WorkMail organization\. For more information, see [Disabling mailbox](https://technet.microsoft.com/en-us/library/jj863434(v=exchg.150).aspx) and [Enabling mail users](https://technet.microsoft.com/en-us/library/aa996549(v=exchg.150).aspx) on Microsoft TechNet\.

1. Send a test email to the user \(in the example above, **workmailuser@yourdomain\.com**\)\. If email routing has been enabled correctly, the user should be able to log in to their Amazon WorkMail mailbox and receive the email\.

**Note**  
Microsoft Exchange remains the primary server for incoming email as long as you would like to have interoperability between the two environments\. To ensure interoperability with Microsoft Exchange, the DNS records shouldn't be updated to point to Amazon WorkMail until later\.

## Post setup configuration<a name="post_setup"></a>

The above steps move a user mailbox from Microsoft Exchange Server to Amazon WorkMail, while keeping the user in Microsoft Exchange as a contact\. Because the migrated user is now an external mail user, Microsoft Exchange Server imposes additional constraints\. There may also be additional configuration requirements to complete the migration\.
+ The user might not be able to send emails to groups by default\. To enable this functionality, you must add the user to a safe sender list for all groups\. For more information, see [Delivery management](https://technet.microsoft.com/en-us/library/bb123722.aspx#deliverymanagement) on Microsoft TechNet\.
+ The user might not be able to book resources\. To enable this functionality, you must set the `ProcessExternalMeetingMessages` of all of the resources that the user needs to access\. For more information, see [Set\-CalendarProcessing](https://technet.microsoft.com/en-us/library/dd335046.aspx) on Microsoft TechNet\.

## Mail client configuration<a name="mail_client_config"></a>

Some mail clients don't switch seamlessly to Amazon WorkMail\. These clients require the user to perform additional setup steps\. Different mail clients require different actions to be taken\.
+ Microsoft Outlook on Windows – Requires Outlook to be restarted\. At startup, you are required to choose whether to keep using the old mailbox or use a temporary mailbox\. Choose the temporary mailbox option\. Then, reconfigure the Microsoft Exchange mailbox\.
+ Microsoft Outlook on MacOS – When Outlook is restarted, it will prompt the following message: **Outlook was redirected to server *orgname*\.awsapps\.com\. Do you want this server to configure your settings?** Accept the suggestion\.
+ Mail on iOS – The mail app stops receiving emails and generates a **can't get mail** error\. Recreate and reconfigure the Microsoft Exchange mailbox\.