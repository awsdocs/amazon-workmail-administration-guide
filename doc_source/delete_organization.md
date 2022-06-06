# Deleting an organization<a name="delete_organization"></a>

If you no longer want to use Amazon WorkMail for your organization's email, you can delete your organization from Amazon WorkMail\. 

**Note**  
This operation can't be undone\. You won't be able to recover your mailbox data after an organization is deleted\.

**To delete an organization**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select the organization to delete and choose **Delete**\.

1. For **Delete organization**, choose whether to delete or keep the existing user directory, and then enter the name of the organization\.

1. Choose **Delete organization**\.

**Note**  
If you didn't provide your own directory for Amazon WorkMail, we'll create one for you\. If you keep this existing directory when you delete the organization, you will be charged for it unless it is being used by Amazon WorkMail, Amazon WorkDocs, or WorkSpaces\. For pricing information, see [Other directory types pricing](https://aws.amazon.com/directoryservice/other-directories-pricing/)\.  
In order to delete the directory, it can't have any other AWS applications enabled\. For more information, see [Deleting a Simple AD directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/simple_ad_delete.html) or [Deleting an AD Connector directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ad_connector_delete.html) in the *AWS Directory Service Administration Guide*\.

You may get an invalid Amazon Simple Email Service \(Amazon SES\) rule set error message when you attempt to delete an organization\. If you receive this error, edit the Amazon SES rule in the Amazon SES console and remove the invalid rule set\. The rule that you edit should have your Amazon WorkMail organization ID in the rule name\. For more information about editing Amazon SES rules, see [Creating receipt rules](https://docs.aws.amazon.com/ses/latest/dg/receiving-email-receipt-rules-console-walkthrough.html) in the *Amazon Simple Email Service Developer Guide*\.

If you need to figure out which rule set is not valid, save the rule first\. An error message appears for the rule set\. 