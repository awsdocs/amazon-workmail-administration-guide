# Managing user accounts<a name="manage-users"></a>

Amazon WorkMail includes tools and options for managing user accounts\. You can create users, enable existing users, edit email addresses and create email aliases, edit user details, and reset user passwords\.

**Topics**
+ [Creating users](#add_new_user)
+ [Enabling existing users](#enable_existing_user)
+ [Disabling user accounts](#disable-users)
+ [Editing user email addresses](#edit_user_email_addresses)
+ [Editing user details](#edit_user_details)
+ [Resetting user passwords](#reset_user_password)
+ [Troubleshooting Amazon WorkMail password policies](#password-policies)

## Creating users<a name="add_new_user"></a>

When you create users, Amazon WorkMail automatically creates mailboxes for them\. Users can log in and access their mail from the Amazon WorkMail web application, their mobile device, or by using Microsoft Outlook on macOS or PC\.

**To create a user**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the organization to which you want to add users\.

1. In the navigation pane, choose **Users**, and then choose **Create User**\.

   The **Create a user** screen appears\.

1. Under **User details**, in the **User name** field, enter the user's name\. The name also appears in the **Email address** box\. If you want the user to have a different email address from their user name, you can edit the **Email address** field\.

1. \(Optional\) Enter the user's first and last name in the **First name** and **Last name** boxes\. 

1. In the **Display name** box, the enter the user's display name\.

1. Under **Email setup**, accept the email alias in the **Email address** box or enter another one\. Then, enter the user's password in the **Password** and **Repeat password** boxes\.Finally, choose **Create user**\.

## Enabling existing users<a name="enable_existing_user"></a>

When you integrate Amazon WorkMail with your corporate Active Directory, or you already have users available in your Simple AD directory, you can enable those users in Amazon WorkMail\. You also follow these steps to reenable a user whose account was disabled\. 

**To enable an existing directory user**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the organization for which you want to enable users\. 

1. In the navigation pane, choose **Users**\.

   A list of tthe group's users appears\. User accounts in the enabled, disabled, and system user states are shown in the list\.

1. From the list of users with disabled accounts, select the checkboxes for the users that you want to enable, and then choose **Enable**\.

   The **Enable users** dialog box appears\.

1. As needed, review and change the primary email address for each user, and then choose **Enable**\.

## Disabling user accounts<a name="disable-users"></a>

You can disable any user account in a group at any time\. When you disable an account, it immediately becomes inaccessible\. User accounts that have been disabled for longer than 30 days will have their inbox deleted from Amazon WorkMail\.

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the organization that contains the users that you want to disable\.

1. In the navigation pane, choose **Users**\.

   A list of all users appears, showing accounts that are in the enabled, disabled, and system user states\.

1. From the list of enabled users, select the checkboxes for the accounts that you want to disable, and then choose **Disable**\.

   The **Disable users** dialog box appears\.

1. Choose **Disable**\.

## Editing user email addresses<a name="edit_user_email_addresses"></a>

When you edit a user email address, you can do the following: 
+ Assign email addresses to a user
+ Assign email aliases to a user
+ Set a new default email address for the user

When you assign addresses to a user, Amazon WorkMail uses the default email address to send outgoing email\. When you assign email aliases, the user can send and receive email from a different address or domain\. For more information, refer to [Send as an alias](https://docs.aws.amazon.com/workmail/latest/userguide/send_alias.html)\.

**To edit email addresses**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the organization that you want to use\.

1. In the navigation pane, choose **Users**, and then choose the desired user name\.
**Note**  
Be sure to choose the name, and not select the checkbox next to the name\. You must choose the name to open the **User details** page\.

   The **User details** page appears\.

1. Choose **Edit**\.

   The **Edit user** screen appears\.

1. Under **Email address**, choose **Add alias**, and then do one of the following:
   + To add an email address, enter an alias in the left\-hand box\. Then choose a domain from the list of available domains\.
   + To add an alias, enter the alias in the left\-hand box\. Don't change the domain\.
   + To set a new email address, enter the desired address in the **Primary email address to be used for this user** box\.

1. Repeat step 5 as needed to enter more addresses or aliases\. When you are finished, choose **Save changes**\.

## Editing user details<a name="edit_user_details"></a>

When you edit a user's details, you can change the following: 
+ **Personal data** – Names, email addresses, phone numbers, and other personal details\.
+ **Mailbox quotas \(sizes\)** – Quotas can range from 1 MB to 51,200 MB \(50 GB\)\. Amazon WorkMail notifies users when they reach 90 percent of their quota\. Also, changing a user's mailbox quota won't affect pricing\. For more information about pricing, refer to [Amazon WorkMail Pricing](http://aws.amazon.com/workmail/pricing/)\.
+ **Mobile device access **– Remove and wipe devices, and view device details\.
+ **Mailbox access permissions** – Grant users permission to use a mailbox, and grant users different levels of access to the mailbox\. 

**Note**  
If you integrate Amazon WorkMail with an AD Connector directory, you can't edit these details from the AWS Management Console\. Instead, you must edit them using your Active Directory management tools\. Limitations apply when your organization is in interoperability mode\. For more information, see [Limitations in interoperability mode](interoperability.md#interop_limitations)\.

**To edit a user's details**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the organization that you want to use\.

1. In the navigation pane, choose **Organizations**, and then choose the organization that you want to use\.

1. In the navigation pane, choose **Users**, and then choose the name of the user to edit\.

1. Do any of the following: 

   **To edit personal data**

   1. In the **User details** section, choose **Edit**\.

   1. Under **User details**, enter or change the user's personal information as needed\. 

   1. When finished, choose **Save changes**\.

   **To edit mailbox quotas**

   1. Under **User details**, choose the **Quota** tab, and then choose **Edit**\.

   1. In the **Update mailbox quota** box, enter a size for the mailbox\. You can enter values from **1** to **51200**\.

   1. Choose **Save**\.

   **To manage mobile device data**
**Note**  
To manage mobile devices, your users first need to connect their devices to your instance of Amazon WorkMail\. For information about connecting mobile devices, refer to [Setting up mobile device clients for Amazon WorkMail](https://docs.aws.amazon.com/workmail/latest/userguide/mobile-client.html)\.

   1. Under **User details**, choose the **Mobile devices** tab\.

   1. To see a current list of devices, choose **Refresh**\.

   1. To view a device's details, choose the device name from the **Device ID** column\.

   1. To remove or wipe the device, choose the radio button next to the device name, and then choose **Remove** or **Wipe** as needed\.

   1. In the dialog box that appears, confirm the removal or wipe operation\. Remember that users will reappear when they sync their devices with Amazon WorkMail again\. 

   **To edit mailbox permissions**

   1. Choose the **Permissions** tab\.

   1. Do one of the following:

      1. To add permissions, choose **Add permissions**\. Open the **Add new permissions** list and choose a user or group, choose the permission settings for the user or group, and then choose **Save**\.

      1. To edit a user's permissions, choose the button next to the user's name\. Choose **Edit**, select the desired options, and then choose **Save**\.

      For more information about the permission options, refer to [Working with mailbox permissions](mail_perms_overview.md)\.

   1. To remove all permissions, choose **Remove**, then confirm the removal\.

## Resetting user passwords<a name="reset_user_password"></a>

If a user forgets their password or has trouble signing in to Amazon WorkMail, you can reset their password\. 

**Note**  
If you've integrated Amazon WorkMail with an AD Connector directory, you must reset the user password in Active Directory\.



**To reset a user password**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the name of your organization\.

1. In the navigation pane, choose **Users**\.

1. In the list of users, select the checkbox next to the name of the user, and then choose **Reset password**\.

1. In the **Reset Password** dialog box, enter the new password, and then choose **Reset**\.

## Troubleshooting Amazon WorkMail password policies<a name="password-policies"></a>

If resetting the password is unsuccessful, verify that the new password meets the password policy requirements\.

The password policy requirements depend on which directory type your Amazon WorkMail organization uses\.

**Amazon WorkMail directory and Simple AD directory password policy**  
By default, passwords for an Amazon WorkMail directory or Simple AD directory must be:


+ Non\-empty
+ At least eight characters
+ Less than 64 characters
+ Composed of Basic Latin or Latin\-1 supplement characters

Passwords must also contain characters from three out of five of the following groups:
+ Uppercase characters
+ Lowercase characters
+ Numerical digits \(0 through 9\)
+ Special characters \(for example, <, \~, or \!\)
+ Latin\-1 supplement characters \(for example, é, ü, or ñ\)

Amazon WorkMail directory password policies can't be changed\.

To change a Simple AD password policy, use the AD administration tools on an Amazon Elastic Compute Cloud \(Amazon EC2\) Windows instance of your Simple AD directory\. For more information, see [Installing the Active Directory administration tools](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/simple_ad_install_ad_tools.html) in the *AWS Directory Service Administration Guide*\.

**AWS Managed Microsoft AD Directory password policy**  
For information about the default password policy for an AWS Managed Microsoft AD directory, see [Manage Password Policies for AWS Managed Microsoft AD](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_password_policies.html) in the *AWS Directory Service Administration Guide*\.

**AD Connector password policy**  
AD Connector uses the password policy of the Active Directory domain that it is connected to\. See the documentation for your Active Directory domain for more information on password policy settings\.