# Restore Disabled Mailboxes<a name="restore_deleted_mailbox"></a>

Amazon WorkMail retains disabled mailboxes for 30 days before permanently removing them\. To restore a mailbox, use the same steps as enabling an existing user\.

**Important**  
Mailboxes cannot be restored if the organization containing them has been deleted\. To restore a user's disabled mailbox, the user must be still in the directory\. If the user isn't in the directory or if you've re\-created them, the mailbox cannot be restored because each mailbox is linked to a unique user ID\.

**To restore a deleted mailbox**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select your organization's alias\.

1. In the navigation pane, choose **Users** to see a list of enabled, disabled, and system users\.

1. From the list of disabled users, select the users to enable and choose **Enable user**\.

1. In the **Enable user\(s\)** dialog box, review the primary email address of the user and choose **Enable**\.