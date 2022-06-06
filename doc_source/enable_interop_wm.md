# Configure availability settings on Amazon WorkMail<a name="enable_interop_wm"></a>

Configure availability settings on Amazon WorkMail and Microsoft Exchange to enable bidirectional sharing of calendar free/busy information\.

**To configure availability settings in the console**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. To do so, open the **Select a region** list, located to the right of the search box, then choose the desired Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of an organization\.

1. In the navigation pane, choose **Organization settings**, and then choose the **Interoperability** tab\. 

1. Choose **Add availability setting**, and then enter the following information:
   + **Using Microsoft Outlook:**

     1. Log in to Microsoft Outlook on Windows for any user on your Exchange environment\.

     1. Hold the **Ctrl** key and open the context \(right\-click\) menu on the Microsoft Outlook icon in the task bar\.

     1. Choose **Test E\-mail AutoConfiguration**\.

     1. Enter the Microsoft Exchange user’s email address and password, and choose **Test**\.

     1. From the Results window, copy the value for the **Availability Service URL**\.
   + **Using PowerShell:**

     1. At the PowerShell prompt, run the following command:

       `Get-WebServicesVirtualDirectory |Select name, *url* | fl`

1. Choose **Save**\.