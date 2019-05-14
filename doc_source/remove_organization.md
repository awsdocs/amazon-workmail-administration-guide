# Removing an Organization<a name="remove_organization"></a>

If you no longer want to use Amazon WorkMail for your organization's email, you can delete your organization from Amazon WorkMail\. 

**Note**  
This operation cannot be undone, and you will not be able to recover your mailbox data\.

**To remove an organization**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the Region\. From the navigation bar, select the appropriate Region\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select the organization to remove and choose **Remove**\.

1. For **Remove organization**, enter the name of the organization, and then choose whether to keep the existing user directory or delete it\.

1. Choose **Remove**\.

**Note**  
If you didn't provide your own directory for Amazon WorkMail, we created one for you\. If you keep this existing directory when you remove the organization, you will be charged for it unless it is being used by Amazon WorkMail, Amazon WorkDocs, or Amazon WorkSpaces\. For pricing information, see [Other Directory Types Pricing](https://aws.amazon.com/directoryservice/other-directories-pricing/)\.  
In order to delete the directory, it cannot have any other AWS applications enabled\. For more information, see [Deleting a Simple AD Directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/cloud_delete.html) or [Deleting an AD Connector Directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/connect_delete.html) in the *AWS Directory Service Administration Guide*\.

If an invalid Amazon SES rule set error message appears when you're attempting to remove an organization, edit the Amazon SES rule in the Amazon SES console and remove the invalid rule set\. The rule that you edit should have your Amazon WorkMail organization ID in the rule name\. For more information about editing Amazon SES rules, see [Editing a Receipt Rule](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/receiving-email-managing-receipt-rules.html#receiving-email-managing-receipt-rules-edit) in the *Amazon Simple Email Service Developer Guide*\.

If you need to figure out which rule set is invalid, save the rule first\. An error message appears for the invalid rule set\. 