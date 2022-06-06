# Using email journaling with Amazon WorkMail<a name="journaling_overview"></a>

You can set up journaling to record your email communication, using integrated third\-party archiving and eDiscovery tools\. This ensures that email storage compliance regulations for privacy protection, data storage, and information protection are met\.

## Using journaling<a name="using_journaling"></a>

Amazon WorkMail journals all email messages that are sent to any user in the specified organization, as well as all email messages sent by users in that organization\. A copy of all email messages is sent to an address specified by the system administrator, in a format called `journal record`\. This format is compatible with Microsoft email programs\. There is no additional charge for email journaling\.

Two email addresses are used for email journaling—a journaling email address and a report email address\. The journaling email address is the address of a dedicated mailbox or third\-party device that is integrated with your account, where journal reports are sent\. The report email address is the address of your system administrator, where notifications of failed journal reports are sent\. 

All journal records are sent from an email address that is automatically added to your domain and looks like the following\. 

```
amazonjournaling@yourorganization.awsapps.com
```

 There is no mailbox associated with this address, and you won't be able to create one using this name or address\. 

**Note**  
don't delete the following domain record from the Amazon Simple Email Service \(Amazon SES\) console, or email journaling stops functioning\.  

```
yourorganization.awsapps.com
```

Every incoming or outgoing email message generates one journal record, regardless of the number of recipients or user groups\. Email that fails to generate a journal record generates an error notification, which is sent to the report email address\.

**To enable email journaling**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the name of your organization\.

1. In the navigation pane, **Organization settings**, choose the **Journaling** tab, and then choose **Edit**\.

1. Move the **Journaling status** slider to the on position\.

1. in the **Journaling email address** box, enter the email address given by your email journaling provider\.
**Note**  
We recommend using a dedicated journaling provider\.

1. In the **Report email address**, enter the email administrator's address\.

1. Choose **Save**\. The changes apply immediately\.