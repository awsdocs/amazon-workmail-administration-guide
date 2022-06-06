# Working with mailbox permissions<a name="mail_perms_overview"></a>

You can use mailbox permissions in Amazon WorkMail to grant users and groups the right to work in other users' mailboxes\. Mailbox permissions apply to an entire mailbox\. They enable multiple users to access the same mailbox without sharing that mailbox's credentials\. Users with mailbox permissions can read and modify mailbox data and send email from the shared mailbox\.

**Note**  
Users with permissions to a mailbox belonging to a user hidden from the global address list can still access the hidden user's mailbox\.

The following list shows the permissions that you can grant:
+ **Full Access** – Enables full read and write access to the mailbox, including permissions to modify folder\-level permissions\.
**Note**  
This options is only available for users\. Groups can't be granted full access rights\.
+ **Send On Behalf** – Enables a user or group to send email on behalf of another user\. The mailbox owner appears in the **From:** header, and the sender appears in the **Sender:** header\. 
+ **Send As** – Enables a user or group to send email as the mailbox owner, without showing the actual sender of the message\. The mailbox owner appears in both the **From:** and **Sender:** headers\.
+ **None** – Prevents a user or group from sending emails\.

**Note**  
Granting mailbox permissions to a group extends those permissions to all the members of that group, including members of nested groups\.

When you grant mailbox permissions, the Amazon WorkMail AutoDiscover service automatically updates access to those mailboxes for the users or groups you added\. 

For the Microsoft Outlook client in Windows, users with full access permissions can automatically access the shared mailboxes\. Allow up to 60 minutes for the changes to propagate, and then restart Microsoft Outlook\. 

For the Amazon WorkMail web application and in other email clients, users with full access permissions can manually open the shared mailboxes\. Opened mailboxes stay open, even between sessions, unless the user closes them\.

**Topics**
+ [About mailbox and folder permissions](mail_vs_folder.md)
+ [Managing mailbox permissions for users](enable_mail_perms.md)
+ [Managing mailbox permissions for groups](manage_group_perms.md)