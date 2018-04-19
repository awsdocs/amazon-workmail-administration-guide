# Remove an Organization<a name="remove_organization"></a>

If you no longer want to use Amazon WorkMail for your organization's email, you can delete your organization from Amazon WorkMail\. 

**Note**  
This operation cannot be undone, and you will not be able to recover your mailbox data\.

**To remove an organization**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select the organization to remove and choose **Remove**\.

1. For **Remove organization**, enter the name of the organization, and then choose whether to keep the existing user directory or delete it\.

1. Choose **Remove** to save these changes\.

**Note**  
If you didn't provide your own directory for Amazon WorkMail, then we created one for you\. If you keep this existing directory when you remove the organization, you will be charged for it unless it is being used by Amazon WorkMail, Amazon WorkDocs, or Amazon WorkSpaces\. For pricing information, see [Other Directory Types Pricing](https://aws.amazon.com/directoryservice/other-directories-pricing/)\.  
To delete the directory, it cannot have any other AWS applications enabled\. For more information, see [Deleting a Simple AD Directory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cloud_delete.html) or [Deleting an AD Connector Directory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/connect_delete.html) in the *AWS Directory Service Administration Guide*\.