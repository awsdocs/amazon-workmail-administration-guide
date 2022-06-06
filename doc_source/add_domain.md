# Adding a domain<a name="add_domain"></a>

You can add up to 100 domains to your Amazon WorkMail organization\. When you add a new domain, an Amazon Simple Email Service \(Amazon SES\) sending authorization policy is automatically added to the domain identity policy\. This provides Amazon WorkMail with access to all Amazon SES sending actions for your domain and allows you to redirect email to your domain\. You can also redirect email to external domains\.

**Note**  
As a best practice, you should add aliases for postmaster@ and abuse@ to all your domains\. You can create distribution groups for these aliases if you want specific users in your organization to receive mail sent to these aliases\.

**When you configure your Amazon WorkMail organization with a custom domain, remember the following about your domain's DNS records:**
+ For MX and autodiscover CNAME records, we recommend setting the **Time to Live \(TTL\)** value to 3600\. Reducing the TTL ensures that your mail servers don't use outdated or invalid MX records after you update those records or migrate your mailboxes\.
+ After you create your users and distribution groups, and then successfully migrate your mailboxes, you should update the MX record to start forwarding emails to Amazon WorkMail\. Updates to DNS records can take up to 48 hours to process\. 
+ Some DNS providers automatically append domain names to the ends of DNS records\. Adding a record that already contains the domain name, such as \_amazonses\.example\.com, might result in the duplication of the domain name, resulting in \_amazonses\.example\.com\.example\.com\. To avoid duplicating the domain name in the record name, add a period to the end of the domain name in the DNS record\. This indicates to your DNS provider that the record name is fully qualified and no longer relative to the domain name\. It also prevents the DNS provider from appending an additional domain name\.
+ Copied record names include the domain name\. Depending on which DNS service you use, the domain name might already be added to the domain's DNS record\.
+ After you create a DNS record, choose the refresh icon on the Amazon WorkMail console to see the verification status and record value\. For more information about verifying domains, see [Verifying domains](domain_verification.md)\.
+ We recommend that you configure your domain as the `MAIL FROM` domain\. To enable AutoDiscover for iOS devices, you must configure your domain as the `MAIL FROM` domain\. You can see the status of your `MAIL FROM` domain in the **Enhance deliverability** section of the console\. For more information, see [Configuring a custom MAIL FROM domain](custom-mail-from-domain.md)\.

**To add a domain**

1. Sign in to the AWS Management Console and open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of the organization that you want to add a domain to\.

1. In the navigation pane, choose **Domains**, and then choose **Add domain**\.

1. On the **Add domain** screen, enter a domain name\. Domain names can contain only Basic Latin \(ASCII\) characters\.
**Note**  
If you have a domain that is managed in an Amazon Route 53 public hosted zone, you can choose it from the dropdown menu that appears as you enter a domain name\.

1. Choose **Add domain**\. 

    A page appears and lists the DNS records for the new domain\. The page groups the records into the following sections: 
   + **Domain ownership**
   + **WorkMail configuration**
   + **Improved security**
   + **Improved email delivery**

   Each of these sections contains one or more DNS records, and each record displays a **Status** value\. The following list shows the records and their available status values\.  
**TXT ownership**  
*Verified* – Record resolved and verified\.  
*Pending* – Record not verified yet\.  
*Failed* – Unable to verify ownership\. Record mismatched or unreachable\.  
**MX WorkMail configuration**  
*Verified* – Record resolved and verified\.  
*Missing* – Unable to resolve record\.  
*Inconsistent* – Value does not match expected record\.  
**AutoDiscover**  
*Verified* – Record resolved and verified\.  
*Missing* – Unable to resolve record\.  
*Inconsistent* – Value does not match expected record\.  
The AutoDiscover verification process also checks for correct AutoDiscover setup\. The process verifies the configuration settings for each phase\. A green check mark appears next to **Verified** in the **Status** column when verification finishes\. You can hover over **Verified** and see which of the phases was verified by the process\. For more information about the AutoDiscover phases, see [Enabling AutoDiscover to configure endpoints](autodiscover.md)\.  
DKIM CNAME  
*Verified* – Record resolved and verified\.  
*Pending* – Record not verified yet  
*Failed* – Unable to verify ownership\. Record mismatched or unreachable\.  
For more information about DKIM signing, see [Authenticating email with DKIM in Amazon SES](https://docs.aws.amazon.com/ses/latest/dg/send-email-authentication-dkim.html) in the *Amazon Simple Email Service Developer Guide*\.  
SPF TXT   
*Verified* – Record resolved and verified\.  
*Missing* – Unable to resolve record\.  
*Inconsistent* – Value does not match expected record\.  
For more information about SPF verification, see [Authenticating email with SPF](authenticate_domain.md)\.  
DMARC TXT  
*Verified* – Record resolved and verified\.  
*Missing* – Unable to resolve record\.  
*Inconsistent* – Value does not match expected record  
For more information about DMARC records in Amazon WorkMail, see [Complying with DMARC using Amazon SES](https://docs.aws.amazon.com/ses/latest/dg/send-email-authentication-dmarc.html) in the *Amazon Simple Email Service Developer Guide*\.  
TXT MAIL FROM domain  
*Verified* – Record resolved and verified\.  
*Pending* – Record not verified yet\.  
*Failed* – Unable to verify ownership\. Record mismatched or unreachable\.  
MX MAIL FROM domain  
*Verified* – Record resolved and verified\.  
Missing – Unable to resolve record\.  
*Inconsistent* – Value does not match expected record\.

1. For the next step, choose the appropriate action based on the DNS provider you use\.

****If you use a Route 53 domain****
   + At the top of the page, choose **Update all in Route 53**\.

****If you use another DNS provider****
   + Copy the records and paste them into your DNS provider\. You can copy the records in bulk or one at a time\. To copy records in bulk, choose **Copy all**\. That creates a file zone that you can import into your DNS provider\. To copy records one at a time, choose the overlapping squares next to the record name, and then paste each one into your DNS provider\. 

1. Choose the refresh icon update the **Status** for each record\. This verifies domain ownership and proper configuration of your domain with Amazon WorkMail\.