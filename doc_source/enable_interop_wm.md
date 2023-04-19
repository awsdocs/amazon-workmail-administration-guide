# Configure availability settings on Amazon WorkMail<a name="enable_interop_wm"></a>

Configure availability settings on Amazon WorkMail to enable querying external systems, offering calendaring functionality, and to get calendar free/busy information\. Amazon WorkMail supports two modes of obtaining free/busy information from a remote system:
+ **Exchange Web Services \(EWS\)** — In this configuration, Amazon WorkMail will query an Exchange server or another WorkMail organization for availability information using the EWS protocol\. This is the simplest configuration but requires the Exchange server’s EWS endpoint to be accessible through the public internet\. 
+ **Custom Availability Provider \(CAP\)** — In this configuration, an administrator can configure an AWS Lambda function to obtain user availability information for a given email domain\. Depending on your email server platform, using CAP with Amazon WorkMail offers the following benefits: 
  + Get user availability from internal EWS without the need to open up their firewall for WorkMail\.
  + Get user availability from non\-Exchange or non\-EWS systems, like Google Workspace \(formerly known as G Suite\)\.

**Topics**
+ [Configure an EWS\-based availability provider](#configure_available_settings)
+ [Configuring a Custom Availability Provider](#Configuring_CAP)
+ [Building a Custom Availability Provider Lambda function](building_cap.md)

## Configure an EWS\-based availability provider<a name="configure_available_settings"></a>

To configure an EWS\-based availability settings on the console, complete the following procedure:

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. To do so, open the **Select a region** list, located to the right of the search box, then choose the desired Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of an organization\.

1. In the navigation pane, choose **Organization settings**, and then choose the **Interoperability** tab\. 

1. Choose **Add availability configuration**, and then enter the following information:
   + **Type** — Select EWS\. 
   + **Domain** — The domain for which WorkMail will attempt to query availability information using this configuration\.
   + **EWS URL** — Amazon WorkMail will query this URL to the EWS endpoint\. See the [Getting the EWS URL](#getting_ews_url) section of this guide\.
   + **User email address** — The email address of the user that WorkMail will use to authenticate with to the EWS endpoint\. 
   + **Password** — The password that WorkMail will use to authenticate with to the EWS endpoint\.

1. Choose **Save**\.

### Getting the EWS URL<a name="getting_ews_url"></a>

To get the EWS URL for Exchange using Microsoft Outlook, complete the following procedure:

1. Log in to Microsoft Outlook on Windows for any user on your Exchange environment\.

1. Hold the **Ctrl** key and open the context \(right\-click\) menu on the Microsoft Outlook icon in the task bar\.

1. Choose **Test E\-mail AutoConfiguration**\.

1. Enter the Microsoft Exchange user’s email address and password, and choose **Test**\.

1. From the Results window, copy the value for the **Availability Service URL**\.

To get the EWS URL for exchange using PowerShell, at the PowerShell prompt, execute the following command:

`Get-WebServicesVirtualDirectory |Select name, *url* | fl`

To get the EWS URL for Amazon WorkMail, first, find the EWS domain under [Amazon WorkMail endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/workmail.html)\. Enter the EWS URL — `https://"EWS domain"/EWS/Exchange.asmx` and replace "EWS domain" with your EWS domain\. 

## Configuring a Custom Availability Provider<a name="Configuring_CAP"></a>

To configure a Custom Availability Provider \(CAP\), complete the following procedure:

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. To do so, open the **Select a Region** list, located to the right of the search box, then choose the desired Region\.

1. In the navigation pane, choose **Organizations**, and then choose the name of an organization\.

1. In the navigation panel, choose **Organization settings** and then choose **Interoperability**\.

1. Choose **Add availability configuration**, and then enter the following information:
   + **Type** — Select **CAP Lambda**\.
   + **Domain** — The domain for which WorkMail will attempt to query availability information using this configuration\.
   + **ARN** — The ARN of the Lambda function that will provide the availability information\.

To build a CAP Lambda function, see [Building a Custom Availability Provider Lambda function](building_cap.md)\.