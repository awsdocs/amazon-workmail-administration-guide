# Enabling SMTP gateways<a name="smtp-gateway"></a>

You enable Simple Mail Transfer Protocol \(SMTP\) gateways for use with outbound email flow rules\. Outbound email flow rules let you route email messages sent from your Amazon WorkMail organization through an SMTP gateway\. For more information, see [Outbound email rule actions](email-flows.md#email-flows-rule-outbound)\.

**Note**  
SMTP gateways configured for outbound email flow rules must support Transport Layer Security \(TLS\) v1\.2 using certificates from major certificate authorities\. Only basic authentication is supported\.

**To configure an SMTP gateway**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the name of an organization\.

1. In the navigation pane, choose **Organization settings**\.

   The **Organization settings** page appears and displays a set of tabs\.

1. Choose the **SMTP gateways** tab, then choose **Create gateway**\.

1. Enter the following:
   + **Gateway name** — Enter a unique name\.
   + **Gateway address** — Enter the gateway's host name or IP address\.
   + **Port number** — Enter the gateway's port number\. 
   + **User name** — Enter a user name\.
   + **Password** — Enter a strong password\.

1. Choose **Create**\.

   The SMTP gateway is available for use with outbound email flow rules\.

When you configure an SMTP gateway for use with an outbound email flow rule, outbound messages attempt to match the rule with an SMTP gateway\. The message that match the rule are routed to the corresponding SMTP gateway, which then handles the rest of the email delivery\.

If Amazon WorkMail is unable to reach the SMTP gateway, the system bounces the email message back to the sender\. If this occurs, follow the previous steps to correct the gateway settings\.