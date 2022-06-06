# Disabling interoperability mode and decommissioning your mail server<a name="disable_interop"></a>

After you configure your Microsoft Exchange mailboxes for Amazon WorkMail, you can disable interoperability mode\. If you haven't migrated any users or records, disabling interoperability mode does not affect any of your configurations\.

**Warning**  
Before disabling interoperability mode, ensure that you complete all the required steps\. Failure to do so can result in bounced emails or unintended behavior\. If you have not completed migration, disabling interoperability may cause disruptions to your organization\. You can't undo this operation\.

**To disable interoperability mode support**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and select the organization for which you want to disable interoperability mode\.

1. Under **Organization settings**, choose **Disable interoperability mode**\.

1. In the **Disable interoperability mode** dialog box, enter the name of the organization and choose **Disable interoperability mode**\.

After disabling interoperability support, users and groups that are not enabled for Amazon WorkMail are removed from the address book\. You can still enable any missing user or group using the Amazon WorkMail console, and they are added to the address book\. Resources from Microsoft Exchange can't be enabled and do not appear in the address book until you complete the step below\.
+ **Create resources in Amazon WorkMail** – You can create resources in Amazon WorkMail and then configure delegates and booking options for these resources\. For more information, see [Working with resources](https://docs.aws.amazon.com/workmail/latest/adminguide/resources_overview.html)\.
+ **Create an AutoDiscover DNS record** – Configure an AutoDiscover DNS record for all mail domains in the organization\. This enables users to connect to their Amazon WorkMail mailboxes from their Microsoft Outlook and mobile clients\. For more information, see [Use AutoDiscover to configure endpoints](https://docs.aws.amazon.com/workmail/latest/adminguide/autodiscover.html)\.
+ **Switch your MX DNS record to Amazon WorkMail** – To deliver all incoming emails to Amazon WorkMail, you must switch your MX DNS record to Amazon WorkMail\. Changes to DNS records can take up to 72 hours to propagate to all DNS servers\.
+ **Decommission your mail server** – After you’ve verified that all email is being routed directly to Amazon WorkMail, you can decommission your mail server if you don't intend to use it going forward\.