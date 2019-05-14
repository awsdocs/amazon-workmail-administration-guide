# Tracking Messages<a name="tracking"></a>

Enable email event logging in the Amazon WorkMail console to track email messages for your organization\. Email event logging uses an AWS Identity and Access Management service\-linked role to grant permissions to publish the email event logs to Amazon CloudWatch\. In the event logs, you can use CloudWatch search tools and metrics to track messages and troubleshoot email issues\.

When you enable email event logging using the default settings, Amazon WorkMail completes the following tasks on your behalf:
+ Creates an AWS Identity and Access Management service\-linked role – `AmazonWorkMailEvents`
+ Creates a CloudWatch log group – `/aws/workmail/emailevents/organization-alias`
+ Sets CloudWatch log retention to 30 days

For more information about using IAM service\-linked roles for Amazon WorkMail event logging, see [Using Service\-Linked Roles for Amazon WorkMail](using-service-linked-roles.md)\. For more information about using CloudWatch to monitor Amazon WorkMail, see [Monitoring Amazon WorkMail](monitoring-overview.md)\. 

**To enable email event logging**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. For **Organizations**, choose the alias of your Amazon WorkMail organization\.

1. In the navigation pane, choose **Organization settings**, **Monitoring**\.

1. For **Log settings**, choose **Edit**\.

1. For **Log Events**, select **Enable mail events**\.

1. Do one of the following:

   1. Select **Use default settings**\.

   1. Clear the check box for **Use default settings**, and select a **Destination Log Group** and **IAM Role**\.

1. Select **I authorize Amazon WorkMail to publish logs in my account using this configuration**\.

1. Choose **Save**\.

Turn off email event logging from the Amazon WorkMail console\. If you no longer need to use email event logging, we recommend that you delete the related CloudWatch log group and service\-linked role as well\. For more information, see [Deleting a Service\-Linked Role for Amazon WorkMail](using-service-linked-roles.md#delete-slr)\.

**To turn off email event logging**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. For **Organizations**, choose the alias of your Amazon WorkMail organization\.

1. In the navigation pane, choose **Organization settings**, **Monitoring**\.

1. For **Log settings**, choose **Edit**\.

1. Clear the check box for **Enable mail events**\.

1. Choose **Save**\.