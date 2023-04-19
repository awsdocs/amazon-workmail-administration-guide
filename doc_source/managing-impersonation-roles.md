# Managing impersonation roles<a name="managing-impersonation-roles"></a>

With impersonation roles, administrators configure programmatic access to user's mailboxes without entering the user's credentials\. Services and tools can assume an impersonation role to perform actions in user's mailboxes\. Impersonation is only supported with the EWS protocol\.

## Impersonation roles overview<a name="how-impersonations-work"></a>

To allow impersonation, administrators must create an impersonation role with the following properties: 
+ **Role type** – Choose either **Full access** or **Read only**\. The role type limits the kind of operations a role can perform\.
+ **Rules** – A list of rules that define which users the impersonation role can impersonate\.

Amazon WorkMail evaluates the rules on the following conditions:
+ If any **DENY** rule matches, the policy denies impersonation\. **DENY** rules take precedence over any **ALLOW** rules\.
+ If at least one **ALLOW** rule matches, and no **DENY** rule matches, the policy allows impersonation\.
+ If no rule applies, impersonation is denied\.

**Note**  
To allow impersonation for all users in an Amazon WorkMail organization, create a rule with the **ALLOW** effect and with no conditions\.

**Warning**  
You must create rules to allow an impersonation role to impersonate a user\. If you do not specify rules, an impersonation role can't assume a user's access rights\.

After the impersonation role is created, you can use it to get access to users' mailboxes\. For more information, see [Using impersonation roles](using-impersonation-roles.md)\.

## Security considerations<a name="security-considerations"></a>

The use of impersonation roles creates the potential for security issues within your Amazon WorkMail organization and AWS account\. Here are some of the potential issues to consider when you create an impersonation role:
+ **Transitive permissions** – If user A has access to user B's mailbox, and an impersonation role is allowed to impersonate user A, then this impersonation role can impersonate user A's access permissions and access user’s B mailbox\.
+ **Access control** – You can use access control rules to limit impersonation role access\. For more information, see [Working with access control rules](access-rules.md)\.
+ **IAM policy** – You can assign an `AssumeImpersonationRole` action to a particular Amazon WorkMail organization and impersonation role by using the `workmail:ImpersonationRoleId` condition\. To see an IAM policy example, see [How Amazon WorkMail works with IAM](security_iam_service-with-iam.md)\.

## Creating impersonation roles<a name="creating-impersonation-roles"></a>

You can create impersonation roles from the Amazon WorkMail console\.

**To create an impersonation role**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the Region\. From the navigation bar, choose the Region that meets your needs\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of the organization\.

1. Choose **Impersonation roles**, and then choose **Create role**\.

1. The **Create impersonation role** dialog box appears\. Under **Role**, enter the following information:
   + **Name** – Enter a unique name for the impersonation role\.
   + \(Optional\) **Description** – Enter a description for the impersonation role\.
   + **Role type** – Choose **Read only** or **Full access**\.

1. Under **Rules**, choose **Add rule**\.

1. The **Add rule** dialog box appears\. Enter the following information:
   + **Name** – Enter a unique name for the rule\.
   + \(Optional\) **Description** – Enter a description for the rule\.
   + Under **Effect**, choose **Allow** or **Deny**\. This allows or denies access based on the conditions you select in the following step\.
   + \(Optional\) Under **This rule:**, choose **Matches requests that impersonate the selected users** to include specific users\. Choose **Matches requests that impersonate users other than the selected users** to add users other than the selected users\.

1. Choose **Add rule**\.
**Note**  
Rules are only saved when you save the corresponding role\.

1. Choose **Create role**\.

## Editing impersonation roles<a name="editing-impersonation-roles"></a>

You can edit impersonation roles from the Amazon WorkMail console\.

**To edit an impersonation role**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the Region\. From the navigation bar, choose the Region that meets your needs\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of the organization\.

1. Choose **Impersonation roles**\.

1. Select the impersonation role name you want to edit, then choose **Edit**\.

1. The **Edit impersonation role** dialog box appears\. Under **Role**, enter the following information:
   + **Name** – Enter a unique name for the impersonation role\.
   + \(Optional\) **Description** – Enter a description for the impersonation role\.
   + **Role type** – To give the impersonation role read only access to a user's mailbox, choose **Read only**\. To give the impersonation role rights to read and modify items in a user's mailbox, choose **Full access**\.

1. Under **Rules**, select the rule that you want to edit and choose **Edit**\.

1. The **Edit rule** dialog box appears\. Enter the following information:
   + **Name** – Edit the name of the rule\.
   + \(Optional\) **Description** – Update or enter a description for the rule\.
   + Under **Effect**, choose **Allow** to allow access when the conditions set in the rules are met\. To deny access, choose **Deny**\.
   + \(Optional\) Under **This rule:**, choose **Matches requests that impersonate the selected users** to include specific users\. Choose **Matches requests that impersonate users other than the selected users** to add users other than the selected users\.

1. Choose **Save**\.

1. Choose **Save changes**\.

**Important**  
When you change an impersonation rule, the affected mailboxes can take up to five minutes to update\. During the rule update process, you may observe inconsistent behavior in your mailbox\. However, if you test a role, Amazon WorkMail responds as expected based on the updated rule\. For more information, see [Testing impersonation roles](#testing-impersonation-roles)\.

## Testing impersonation roles<a name="testing-impersonation-roles"></a>

You can test an impersonation role from the Amazon WorkMail console\.

**To test an impersonation role**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the Region\. From the navigation bar, choose the Region that meets your needs\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of the organization\.

1. Choose **Impersonation roles**\.

1. Select the impersonation role that you want to test\.

1. Choose **Test role**\.

   

1. The **Test impersonation role** dialog box appears\. Under **Target user**, select the user for which you want to test the impersonation access\.

1. Choose **Test**\.

## Deleting impersonation roles<a name="deleting-impersonation-roles"></a>

You can delete an impersonation role from the Amazon WorkMail console\.

**To delete an impersonation role**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the Region\. From the navigation bar, choose the Region that meets your needs\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of the organization\.

1. Choose **Impersonation roles**\.

1. Select the impersonation role name you want to delete\.

1. Choose **Delete**\.

1. The **Delete role** dialog box appears\. To confirm deletion, enter the role's name into the dialog box and choose **Delete**\.