# Verifying domains<a name="domain_verification"></a>

You must verify your domain after you add it in the Amazon WorkMail console\. Verifying the domain confirms that you own the domain and will use Amazon WorkMail as the email service for the domain\.

You verify a domain by adding TXT and MX records to it in your DNS service\. TXT records enable you to add notes to your DNS service\. MX records specify the incoming mail server\.

You use the Amazon SES console to create the TXT and MX records, and then you use the Amazon WorkMail console to add the records to your DNS service\. Follow these steps\.



**To create TXT and MX records**

1. Open the Amazon SES console at [https://console\.aws\.amazon\.com/ses/](https://console.aws.amazon.com/ses/)\.

1. In the navigation pane, choose **Domains**, and then choose **Verify a New Domain**\.

   The **Verify a New Domain dialog box appears\.**

1. In the **Domain** box, enter the name of the domain that you created in the [Adding a domain](add_domain.md) section\. 

1. \(Optional\) If you want to use DomainKeys Identified Mail \(DKIM\), select the **Generate DKIM Settings** checkbox\.

1. Choose **Verify This Domain**\.

   The console displays a list of TXT and MX records\.

1. Choose the **Download Record Set as CSV** link, located under the TXT listing\.

   The **Save As** dialog box appears\. Choose a location for the download, and then choose **Save**\.

1. Open the downloaded CSV file and copy all of its contents\. 

Once your create the TXT and MX records, you then add them to your DNS provider\. The following steps use Route 53\. If you use a different DNS provider and you don't know how to add records, consult your provider's documentation\.

1. Sign in to the AWS Management Console and open the Route 53 console at [https://console\.aws\.amazon\.com/route53/](https://console.aws.amazon.com/route53/)\.

1. In the navigation pane, choose **Hosted Zones**\. Then, choose the radio button next to the domain that you want to verify\.

1. From the list of DNS records for your domain, choose **Import zone file**\.

1. Under **Zone file**, paste the copied records into the text box\. A list of the files appears below the text box\.

1. Scroll down to the end of the list and choose **Import**\.

**Note**  
Allow up to 72 hours to complete the verification process\.

## Verifying TXT records and MX records with your DNS service<a name="domain-verification-check-dns"></a>

Confirm that the TXT record that verifies that you own the domain is added correctly to your DNS service\. This procedure uses the [nslookup](http://en.wikipedia.org/wiki/Nslookup) tool, which is available for Windows and Linux\. On Linux, you can also use [dig](http://en.wikipedia.org/wiki/Dig_(command))\.

To use the `nslookup` tool, you must first find the DNS servers that serve your domain\. Then, you query those servers to view the TXT records\. You can query the DNS servers for your domain because those servers contain the most up\-to\-date information for your domain\. This information can take time to propagate to other DNS servers\.

### Use nslookup to verify that your TXT record is added to your DNS service<a name="use-nslookup"></a>

1. Find your domain's name servers:

   1. Open a command prompt \(Windows\) or terminal \(Linux\)\.

   1. Run the following command to list all of the name servers that serve your domain\. Replace *example\.com* with your domain\.

      ```
      1. nslookup -type=NS example.com
      ```

      You'll query one of these name servers in the next step\.

1. Verify that the Amazon WorkMail TXT record is correctly added\.

   1. Run the following command, replacing *example\.com* with your domain, and *ns1\.name\-server\.net* with a name server from Step 1\.

      ```
      1. nslookup -type=TXT _amazonses.example.com ns1.name-server.net
      ```

   1. Review the `"text ="` string shown in the output from nslookup\. Confirm that this string matches the TXT value for your domain in the **Verified Senders** list in the Amazon WorkMail console\. 

      In the following example, you want to see a TXT record for \_amazonses\.example\.com with a value of `fmxqxT/icOYx4aA/bEUrDPMeax9/s3frblS+niixmqk=`\. If you update the record correctly, the command has the following output:

      ```
      1. _amazonses.example.com text = "fmxqxT/icOYx4aA/bEUrDPMeax9/s3frblS+niixmqk="
      ```

### Use dig to verify that your TXT record is added to your DNS service<a name="use-dig"></a>

1. Open a terminal session\.

1. Run the following command to list the TXT records for your domain\. Replace *example\.com* with your domain\.

   ```
   1. dig +short example.com txt
   ```

1. Verify that the string that follows `TXT` in the command's output matches the TXT value you see when you select the domain in the **Verified Senders** list of the Amazon WorkMail console\.

### To use nslookup to verify that your MX record is added to your DNS service<a name="use-nslookup-mx"></a>

1. Find the name servers for your domain:

   1. Open a command prompt\.

   1. Run the following command to list all of the name servers for your domain\.

      ```
      1. nslookup -type=NS example.com
      ```

      You'll query one of these name servers in the next step\.

1. Verify that the MX record is correctly added:

   1. Run the following command, replacing *example\.com* with your domain and *ns1\.name\-server\.net* with one of the name servers you identified in the previous step\.\.

      ```
      1. nslookup -type=MX example.com ns1.name-server.net
      ```

   1. In the output of the command, verify that the string that follows `mail exchange = ` matches one of the following values: 

      **US East \(N\. Virginia\) Region** – `10 inbound-smtp.us-east-1.amazonaws.com`

      **US West \(Oregon\) Region** – `10 inbound-smtp.us-west-2.amazonaws.com`

      **Europe \(Ireland\) Region** – `10 inbound-smtp.eu-west-1.amazonaws.com`
**Note**  
`10` represents the MX preference number or priority\.

### Use dig to verify that your MX record is added to your DNS service<a name="use-dig-mx"></a>

1. Open a terminal session\.

1. Run the following command to list the MX records for your domain\.

   ```
   1. dig +short example.com mx
   ```

1. Verify that the string that follows `MX` matches one of the following values:

   **US East \(N\. Virginia\) Region** – `10 inbound-smtp.us-east-1.amazonaws.com`

   **US West \(Oregon\) Region** – `10 inbound-smtp.us-west-2.amazonaws.com`

   **Europe \(Ireland\) Region** – `10 inbound-smtp.eu-west-1.amazonaws.com`
**Note**  
`10` represents the MX preference number or priority\.

## Troubleshooting domain verification<a name="domain-verification-issues"></a>

To troubleshoot common issues with domain verification, see the following suggestions:

Your DNS service does not allow underscores in TXT record names  
Omit `_amazonses` from the TXT record name\.

You want to verify the same domain multiple times but can't have multiple TXT records with the same name  
If your DNS service does not allow you to have multiple TXT records with the same name, use either of the following workarounds:   
+ \(Recommended\) If your DNS service allows it, assign multiple values to the TXT record\. For example, if your DNS is managed by Amazon Route 53, you can set up multiple values for the same TXT record as follows:

  1. In the Route 53 console, choose the `_amazonses` TXT record that you added when you verified your domain in the first Region\.

  1. For **Value**, press **Enter** after the first value\.

  1. Add the value for the additional Region, and save the record set\.
+ If you only need to verify your domain twice, you can verify it once by creating a TXT record with `_amazonses` in the name, and then create another record without `_amazonses` in the record name\.

The Amazon WorkMail console reports that domain verification has failed  
Amazon WorkMail can't find the necessary TXT record for your DNS service\. Verify that the required TXT record is correctly added to your DNS service by following the procedure in [Verifying TXT records and MX records with your DNS service](#domain-verification-check-dns)\.

Your DNS provider appended the domain name to the end of the TXT record  
Adding a TXT record that already contains the domain name, such as \_amazonses\.example\.com, can result in the duplication of the domain name, such as \_amazonses\.example\.com\.example\.com\. To avoid duplicating the domain name in the record name, add a period to the end of the domain name in the TXT record\. This indicates to your DNS provider that the record name is fully qualified and already has the domain name included in the TXT record\.

Amazon WorkMail reports that the MX record is **Inconsistent**  
When migrating from existing mail servers, the MX record might return a status of **Inconsistent**\. Update your MX record to point to Amazon WorkMail instead of pointing to your previous mail server\. The MX record is also returned as **Inconsistent** when a third\-party email proxy is used along with Amazon WorkMail\. If this is the case, it is safe to ignore the **Inconsistent** warning\.