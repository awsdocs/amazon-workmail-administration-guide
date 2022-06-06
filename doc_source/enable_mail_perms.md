# Managing mailbox permissions for users<a name="enable_mail_perms"></a>

You can use the Amazon WorkMail console to manage mailbox permissions for users, as well as groups\. The following sections explain how to manage permissions for users\. For information about managing permissions for groups, refer to [Managing mailbox permissions for groups](manage_group_perms.md)\.

**Topics**
+ [Adding permissions](#add-permissions)
+ [Editing mailbox permissions for users](#edit_mail_perms)

## Adding permissions<a name="add-permissions"></a>

When you add permissions, you grant one user the right to perform one or more tasks in another user's mailbox\. For example, say that Employee A needs to send messages on behalf of his supervisor, Employee B\. To grant that permission, you go to Employee B's mailbox settings and grant Employee A permission to do the requested task\. 

**To add mailbox permissions**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the Region\. From the navigation bar, choose the Region that meets your needs\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of the organization for which you want to manage permissions\.

1. In the navigation pane, choose **Users**, and then select the name of the user for whom you want to manage permissions\.

1. Choose the **Permissions** tab, and then choose **Add permissions**\.

   The **Add permissions** dialog box appears\.

1. Open the **Add new permissions** list and select the user or group that needs access to the mailbox\.

1. Under **Mailbox permissions** and **Send permissions**, choose the desired options\.

1. Choose **Add**\.

New permissions can take up to five minutes to propagate to users\.

## Editing mailbox permissions for users<a name="edit_mail_perms"></a>

When you edit mailbox permissions for a user, you change the access that others have to that user's mailbox\. Editing mailbox permissions doesn't change access for the mailbox's original user\. 

**To edit mailbox permissions**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the Region\. From the navigation bar, choose the Region that meets your needs\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of the organization for which you want to manage permissions\.

1. In the navigation pane, choose **Users**, and then select the name of the user whose permissions you want to edit\.

1. Choose the **Permissions** tab\.

   A list of the users and groups that have access to the mailbox appears\.

1. Select the radio button next to the user or group that you want to change, then do any of the following:

**To remove a user's permissions**

   1. Choose **Remove**\.

      The **Remove permissions** dialog box appears\.

   1. In the **Remove permissions** dialog box, choose **Remove**\.

**To edit a user's permissions**

   1. Choose **Edit**\.

      The **Edit permissions** dialog box appears\.

   1. Set the permissions as needed, and then choose **Save**\.

**To grant another user permissions to the mailbox**

   1. Choose **Add permissions**\.

      The **Add permissions** dialog box appears\.

   1. Open the **Add new permissions** list and select the user that you want to add\. 

   1. Set the permissions as needed, and then choose **Add**\.

Changes to permissions can take up to five minutes to propagate to users\.