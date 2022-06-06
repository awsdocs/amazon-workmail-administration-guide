# Enforcing DMARC policies on incoming email<a name="inbound-dmarc"></a>

Email domains use Domain Name System \(DNS\) records for security\. They protect your users from common attacks such as spoofing or phishing\. DNS records often include Domain\-based Message Authentication, Reporting, and Conformance \(DMARC\) records, which are set by the domain owner that sends the email\. DMARC records include policies that specify actions to take when an email fails a DMARC check\. You can choose whether to enforce the DMARC policy on emails being sent to your organization\.

New Amazon WorkMail organizations have DMARC enforcement turned on by default\.

**To turn on DMARC enforcement**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the name of your organization\.

1. In the navigation pane, choose **Organization settings**\. The **Organization settings** page appears and displays a set of tabs\.

1. Choose the **DMARC** tab, then choose **Edit**\.

1. Move the **DMARC enforcement** slider to the on position\.

1. Select the checkbox next to **I acknowledge that turning on DMARC enforcement may result in inbound emails being dropped or quarantined based on the sender's domain configuration\.**

1. Choose **Save**\.

**To turn off DMARC enforcement**
+ Follow the steps in the previous section, but move the **DMARC enforcement** slider to the off position\.\.

## Using email event logging to track DMARC enforcement<a name="logging-dmarc"></a>

Turning on DMARC enforcement might result in inbound emails being dropped or marked as spam, depending on how the sender configured their domain\. If a sender misconfigures their email domain, your users might stop receiving legitimate emails\. To check for emails that aren't being delivered to your users, you can enable email event logging for your Amazon WorkMail organization\. Then, you can query your email event logs for inbound emails that are filtered out based on the sender's DMARC policies\. 

Before you use email event logging to track DMARC enforcement, enable email event logging in the Amazon WorkMail console\. To get the most out of your log data, allow some time to pass while email events are logged\. For more information and instructions, see [Turning on email event logging](tracking.md#enable-tracking)\.

**To use email event logging to track DMARC enforcement**

1. In the CloudWatch Insights console, under **Logs**, choose **Insights**\. 

1. For **Select log group\(s\)**, select your Amazon WorkMail organization's log group\. For example, /aws/workmail/events/organization\-alias\.

1. Select a time period to query\.

1. Run the following query: **stats count\(\) by event\.dmarcPolicy \| filter event\.dmarcVerdict == "FAIL"**

1. Choose **Run query**\.

You can also set up custom metrics for these events\. For more information, see [Creating metric filters](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/MonitoringPolicyExample.html)\.