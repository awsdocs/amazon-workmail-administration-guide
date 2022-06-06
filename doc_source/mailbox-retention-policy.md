# Setting mailbox retention policies<a name="mailbox-retention-policy"></a>

You can set mailbox retention policies for your Amazon WorkMail organization\. Retention policies automatically delete email messages from user mailboxes after a time period that you choose\. You can choose which mailbox folders to apply retention policies to\. Also, you can choose whether to set different retention policies for different folders\. Mailbox retention policies apply to the selected folders in all of the user mailboxes in your organization\. Users can't override the retention policies\.

**To set a mailbox retention policy**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of your organization\.

1. Choose **Retention policy**\.

1. For **Folder actions**, next to each mailbox folder that you want to include in the policy, select **Delete** or **Permanently delete**\.

1. Enter the number of days to keep the email messages in each mailbox folder before deleting them\.

1. Choose **Save**\.

Allow 48 hours to apply the retention policies for your organization\. If you choose the **Delete** folder action, users can recover deleted email messages from the Amazon WorkMail web application and supported clients\. If you choose the **Permanently delete** folder action, email messages can't be recovered after they are deleted\.

The number of days a retention policy keeps an item is based on when it was created, modified, or moved\. For example, if a retention policy deletes items after a year, the policy counts retention days from the date you created or last took action on that item\. It is not affected by the date you implemented the retention policy\. 