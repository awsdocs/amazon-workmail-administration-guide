# Adding a Domain<a name="add_domain"></a>

You can add up to 100 domains to your organization\. When you add a new domain, an Amazon SES sending authorization policy is automatically added to the domain identity policy\. This provides Amazon WorkMail with access to all Amazon SES sending actions for your domain and allows you to redirect email to your domain as well as external domains\.

**Important**  
Some DNS providers automatically append the domain name to the end of DNS records\. Adding a record that already contains the domain name \(such as \_amazonses\.example\.com\) might result in the duplication of the domain name \(such as \_amazonses\.example\.com\.example\.com\)\. To avoid duplication of the domain name, add a period to the end of the domain name in the DNS record\. This will indicate to your DNS provider that the record name is fully qualified \(that is, no longer relative to the domain name\), and prevent the DNS provider from appending an additional domain name\.

**Note**  
As a best practice, you should add aliases for postmaster@ and abuse@\. You can create distribution groups for these aliases if you want certain users in your organization to receive mail sent to these aliases\.

**To add a domain**

1. Sign in to the AWS Management Console and open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the **Alias** column, select the name of the organization to which to add a domain\.

1. In the navigation pane, choose **Domains**, **Add domain**\.

1. On the **Add domain** screen, enter the domain name to add,and choose **Add domain**\.

1. On the next screen, in the **Step 1: verify domain ownership** section, the TXT record verifies your ownership of the domain\.

   After all your users and distribution groups are created, and mailboxes are successfully migrated, you can switch the MX record to start delivering email to Amazon WorkMail\. Updates to the DNS record can take up to 72 hours to be processed and made active, however updates are often processed and made active sooner than this\.

1. In the **Step 2: Finalize domain setup** section, the following records are listed:
   + The MX record to deliver incoming email to Amazon WorkMail\.
   + The CNAME autodiscover record that allows users to easily configure their Microsoft Outlook or mobile device knowing only their email address and password\.
   + The CNAME records for DKIM signing\. For more information about DKIM signing, see [Authenticating Email with DKIM](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/dkim.html) in the *Amazon Simple Email Service Developer Guide*\.

   We recommend that you set the Time to Live \(TTL\) to 3600 of the MX and autodiscover CNAME record\. Reducing the TTL ensures that your mail servers don't use outdated or invalid MX records after updating your MX records or migrating your mailboxes\.

   For more information about adding these DNS records to Amazon Route 53, see [Routing Queries to Amazon WorkMail \(Public Hosted Zones Only\)](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-workmail.html) in the *Amazon Route 53 Developer Guide*\.