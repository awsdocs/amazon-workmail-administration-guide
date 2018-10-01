# Migrating to Amazon WorkMail<a name="migration_overview"></a>

You can migrate to Amazon WorkMail from Microsoft Exchange, Microsoft Office 365, G Suite Basic \(formerly Google Apps for Work\), and many other platforms by working with one of our partners\. For more information about our partners, see [Migrate to Amazon WorkMail for Free](https://aws.amazon.com/workmail/details/)\.

**Topics**
+ [Step 1: Create or Enable Users in Amazon WorkMail](#create_enable_users)
+ [Step 2: Migrate to Amazon WorkMail](#prepare_mail_server)
+ [Step 3: Complete the Migration to Amazon WorkMail](#complete_migration)

## Step 1: Create or Enable Users in Amazon WorkMail<a name="create_enable_users"></a>

Before you can migrate your users, you must add the users in Amazon WorkMail to provision the mailbox\. For more information, see [Creating New Users](manage-users.md#add_new_user)\.

## Step 2: Migrate to Amazon WorkMail<a name="prepare_mail_server"></a>

You can work with any of our migration partners to migrate to Amazon WorkMail\. For information about about these providers, see [Amazon WorkMail](https://aws.amazon.com/workmail/details/)\.

To migrate your mailboxes, you can assign an Amazon WorkMail user as the migration administrator\. You can specify the migration administrator in the following ways: 
+ Add the new user **migration\_admin** in the Amazon WorkMail console\. You can also create the user **migration\_admin** in your Active Directory and enable this user for Amazon WorkMail\.
+ In the Amazon WorkMail console, on the **Organizations settings** screen, under **Migration settings**, choose **Edit**, and then specify a user that you've designated as the migration administrator in the **migration\_admin** field\.

## Step 3: Complete the Migration to Amazon WorkMail<a name="complete_migration"></a>

After you have migrated your email accounts to Amazon WorkMail, verify your DNS records and configure your desktop and mobile clients\.

**To complete migration to Amazon WorkMail**

1. Verify that all DNS records are updated and that they point to Amazon WorkMail\. For more information about the required DNS records, see [Adding a Domain](add_domain.md)\. 
**Note**  
The DNS record update process may take several hours\. If any new items appear in a source mailbox while the MX records are being changed, run the migration tool again to migrate new items after the DNS records are updated\.

1. For more information about configuring your desktop or mobile clients to use Amazon WorkMail, see [Connect Microsoft Outlook to Your Amazon WorkMail Account](https://docs.aws.amazon.com/workmail/latest/userguide/connect_mail_client.html) in the *Amazon WorkMail User Guide*\.