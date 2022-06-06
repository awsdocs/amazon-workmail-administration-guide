# Creating email flow rules<a name="create-email-rules"></a>

Email flow rules apply [rule actions](email-flows.md#email-flows-rule-actions) to incoming and outgoing email messages\. The actions apply when messages match a specified [pattern](email-flows.md#email-flows-patterns)\. New email flow rules take effect immediately\.

**To create email flow rules**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the name of an organization\.

1. In the navigation pane, choose **Organization settings**\.

   The **Organization settings** page appears and displays a set of tabs\. From this page, you can create inbound or outbound rules\. The following steps explain how to create both types\.

**To create inbound rules**

   1. Choose the **Inbound rules** tab and then choose **Create**\.

   1. In the **Rule name** box, enter a unique name\.

   1. Under **Action**, open the list and select an action\. Each item in the list contains a description, and some provide **Learn more** links\.
**Note**  
If you choose the **Run Lambda** action, additional controls appear: For information about using those controls, see the next section, [Configuring AWS Lambda for Amazon WorkMail](lambda.md)\. 

   1. Under **Sender domains or addresses**, enter the sender domains or addresses to which you want the rule to apply\.

   1. Under **Destination domains or addresses**, enter any combination of destination domains and email addresses\.

   1. Choose **Create**\.

**To create outbound rules**

   1. Choose the **Outbound rules** tab and choose **Create**\.

   1. In the **Rule name** box, enter a unique name\.

   1. Under **Action**, open the list and select an action\. Each item in the list contains a description, and some provide **Learn more** links\.
**Note**  
If you choose the **Run Lambda** action, additional controls appear\. For information about using those controls, see the next section, [Configuring AWS Lambda for Amazon WorkMail](lambda.md)\.

   1. Under **Sender domains or addresses**, enter any combination of valid sender domains and email addresses\.

   1. Under **Destination domains or addresses**, enter any combination of valid destinations domains and email addresses\.

   1. Choose **Create**\.

   You can test the new email flow rule that you created\. For more information, see [Testing an email flow rule](test-email-flow-rule.md)\.