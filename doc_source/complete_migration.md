# Step 3: Complete the Migration to Amazon WorkMail<a name="complete_migration"></a>

After you have migrated your email accounts to Amazon WorkMail, you need to verify your DNS records and configure your desktop and mobile clients\.

**To complete migration to Amazon WorkMail**

1. Verify that all DNS records are updated and that they point to Amazon WorkMail\. For more information about the required DNS records, see [Add a Domain](add_domain.md)\. 
**Note**  
The DNS record update process may take several hours\. If any new items appear in a source mailbox while the MX records are being changed, you can re\-run the migration tool to migrate new items after the DNS records are updated\.

1. Configure your desktop and mobile clients to use Amazon WorkMail\. For more information about configuring your desktop or mobile clients, see [Connect Microsoft Outlook to Your Amazon WorkMail Account](http://docs.aws.amazon.com/workmail/latest/userguide/connect_mail_client.html) in the *Amazon WorkMail User Guide*\.