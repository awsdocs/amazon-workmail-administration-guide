# Managing User Accounts<a name="manage-users"></a>

Create new users or enable existing users and edit user email addresses, create user email aliases, edit user details, and reset user passwords from Amazon WorkMail\.

**Topics**
+ [Creating New Users](#add_new_user)
+ [Enabling Existing Users](#enable_existing_user)
+ [Editing User Email Addresses](#edit_user_email_addresses)
+ [Editing User Details](#edit_user_details)
+ [Resetting User Passwords](#reset_user_password)

## Creating New Users<a name="add_new_user"></a>

When you create new users, Amazon WorkMail creates mailboxes for them\. Users can log in and access their mail from the Amazon WorkMail web application, mobile device, or Microsoft Outlook on macOS or PC\.

**To create a new user**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select your organization's alias\.

1. In the navigation pane, choose **Users** to see a list of all users in the directory\. This includes enabled, disabled, and system users as defined by the underlying directory\.

1. To create a new user, choose **Create User**\.

1. On the **Add the details for your new user** screen, enter the user's first and last name, username, and display name and then choose **Next**\.

1. On the **Set up email address and password** screen, enter the user's email address and password, and choose **Add user**\.

## Enabling Existing Users<a name="enable_existing_user"></a>

When Amazon WorkMail is integrated with your corporate Active Directory or you already have users available in your Simple AD directory, you can enable these users in Amazon WorkMail\.

**To enable an existing directory user**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select your organization's alias\.

1. In the navigation pane, choose **Users** to see a list of all the users in the directory, including enabled, disabled, and system users\.

1. From the list of disabled users, select the users to enable and choose **Enable user**\.

1. In the **Enable user\(s\)** dialog box, review the primary email address and choose **Enable**\.

## Editing User Email Addresses<a name="edit_user_email_addresses"></a>

You can assign multiple email addresses to a single user and the default email address is used as the default sending address for outgoing email\. 

You can also add one or more email aliases, which can be used to send or receive email from a different address or domain\. For more information, see [Send as an Alias](https://docs.aws.amazon.com/workmail/latest/userguide/send_alias.html)\.

**To edit a user's email address**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select your organization's alias\.

1. In the navigation pane, choose **Users**, and then in the list of users, select the name of the user to edit\.

1. On the **General** tab, choose **Edit**, **Add email address**, and then type the email address to add to this user\.

1. To set the new email address as the default, choose **Set as default**\.

## Editing User Details<a name="edit_user_details"></a>

You can edit a user's first and last name, email address, display name, address, phone number, and company details\.

**Note**  
If you are integrating Amazon WorkMail with an AD Connector directory, you can't edit these details from the AWS Management Console\. Instead, you must edit them using your Active Directory management tools\.

**To edit a user's details**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select your organization's alias\.

1. In the navigation pane, choose **Users** and select the name of the user to edit\.

1. On the **General** tab, choose **Edit**, and then update any of the fields as appropriate\.

## Resetting User Passwords<a name="reset_user_password"></a>

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