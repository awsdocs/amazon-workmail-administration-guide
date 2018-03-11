# Reset User Passwords<a name="reset_user_password"></a>

If a user forgets a password or is having trouble signing in to Amazon WorkMail, you can reset the password\. If you are integrating Amazon WorkMail with an AD Connector directory, you have to reset the user password in Active Directory\.

**To reset a user password**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select your organization's alias\.

1. In the navigation pane, choose **Users**\.

1. In the list of users, select the name of the user to edit and choose **Reset password**\.

1. In the **Reset Password** dialog box, type the new password and choose **Reset**\.
**Note**  
Amazon WorkMail enforces password policies, but additional policies may be applicable\. If the attempt to reset the password is unsuccessful, verify any password policies that are set in the [directory](https://aws.amazon.com/directoryservice)\.