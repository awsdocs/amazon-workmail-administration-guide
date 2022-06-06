# Editing your organization's mobile device policy<a name="edit_mobile_policy"></a>

You can edit your organization's mobile device policy to change the way that mobile devices interact with Amazon WorkMail\.

**To edit your organization's mobile device policy**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a region** list and choose a Region\. For more information, see [Region Name and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of your organization\.

1. In the navigation pane, choose **Mobile Policies**, and then on the **Mobile policy** screen, choose **Edit**\.

1. Update any of the following as necessary:

   1. **Require encryption on device**: Encrypt email data on the mobile device\.

   1. **Require encryption on storage card**: Encrypt email data on the mobile device's removable storage\.

   1. **Password required**: Require a password to unlock a mobile device\.

   1. **Allow simple password**: Use the device's PIN as the password\.

   1. **Minimal password length**: Set the number of characters required for a valid password\.

   1. **Require alphanumeric password:** Require passwords that consist of letters and numbers\.

   1. **Number of failed attempts allowed**: Specify the number of failed login attempts that are allowed before the user is locked out of their account\.

   1. **Password expiration**: Specify the number of days before a password expires and must be changed\.

   1. **Enable screen lock**: Specify the number of seconds that must elapse without user input to lock the user's screen\.

   1. **Enforce password history**: Specify the number of passwords that can be entered before repeating the same password\.

1. Choose **Save**\.