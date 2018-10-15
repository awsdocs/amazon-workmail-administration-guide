# Verifying Domains<a name="domain_verification"></a>

To verify a domain with Amazon WorkMail, initiate the process using the Amazon WorkMail console, and then publish a TXT record to your DNS server as described in [Verifying Domains in Amazon SES](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/verify-domains.html) in the *Amazon Simple Email Service Developer Guide*\. The Amazon WorkMail console allows you to check domain verification status and domain record values\. For more information, see [Adding a Domain](add_domain.md)\. 

This section contains the following topics that might help you if you encounter problems:
+ To verify that the TXT record is correctly published to your DNS server, see [How to Check Domain Verification Settings](#domain-verification-check-dns)\.
+ For some common problems you may encounter when you attempt to verify your domain with Amazon WorkMail, see [Common Domain Verification Problems](#domain-verification-issues)\.

## How to Check Domain Verification Settings<a name="domain-verification-check-dns"></a>

You can check that your Amazon WorkMail domain verification TXT record is published correctly to your DNS server by using the following procedure\. This procedure uses the [nslookup](http://en.wikipedia.org/wiki/Nslookup) tool, which is available for Windows and Linux\. On Linux, you can also use [dig](http://en.wikipedia.org/wiki/Dig_(command))\.

The commands in these instructions were executed on Windows 7, and the example domain we use is *example\.com*\.

In this procedure, you first find the DNS servers that serve your domain, and then query those servers to view the TXT records\. You query the DNS servers that serve your domain because those servers contain the most up\-to\-date information for your domain, which can take time to propagate to other DNS servers\.

**To verify that your domain verification TXT record is published to your DNS server**

1. Find the name servers for your domain:

   1. Open a command prompt\. To open a command prompt on Windows 7, choose **Start** and type **cmd**\. On Linux\-based operating systems, open a terminal window\.

   1. At the command prompt, type the following, where *<domain>* is your domain\. This lists all of the name servers that serve your domain\. 

      ```
      1. nslookup -type=NS <domain>
      ```

      If your domain was *example\.com*, this command would look like:

      ```
      1. nslookup -type=NS example.com
      ```

      The command's output list the name servers that serve your domain\. You query one of these servers in the next step\.

1. Verify that the TXT record is correctly published:

   1. At the command prompt, type the following, where *<domain>* is your domain, and *<name server>* is one of the name servers you found in step 1\.

      ```
      1. nslookup -type=TXT  _amazonses.<domain> <name server>
      ```

      In this *example\.com* example, if the name server in step 1 was called *ns1\.name\-server\.net*, you would type the following:

      ```
      1. nslookup -type=TXT  _amazonses.example.com ns1.name-server.net
      ```

   1. In the output of the command, verify that the string that follows `text = ` matches the TXT value you see when you select the domain in the Verified Senders list of the Amazon WorkMail console\. 

      In the example, you are looking for a TXT record under *\_amazonses\.example\.com* with a value of `fmxqxT/icOYx4aA/bEUrDPMeax9/s3frblS+niixmqk=`\. If the record is correctly published, the command should have the following output:

      ```
      1. _amazonses.example.com text = "fmxqxT/icOYx4aA/bEUrDPMeax9/s3frblS+niixmqk="
      ```

**To verify that your domain verification MX record is published to your DNS server**

1. Find the name servers for your domain:

   1. Open a command prompt\. To open a command prompt on Windows 7, choose **Start** and type **cmd**\. On Linux\-based operating systems, open a terminal window\.

   1. At the command prompt, type the following, where *<domain>* is your domain\. This lists all of the name servers that serve your domain\. 

      ```
      1. nslookup -type=NS <domain>
      ```

      If your domain was *example\.com*, this command would look like:

      ```
      1. nslookup -type=NS example.com
      ```

      The command's output lists the name servers that serve your domain\. You query one of these servers in the next step\.

1. Verify that the MX record is correctly published:

   1. At the command prompt, type the following, where *<domain>* is your domain, and *<name server>* is one of the name servers you found in step 1\.

      ```
      1. nslookup -type=MX <domain> <name server>
      ```

      In the *example\.com* example, if the name server in step 1 is called *ns1\.name\-server\.net*, you would type the following:

      ```
      1. nslookup -type=MX example.com ns1.name-server.net
      ```

   1. In the output of the command, verify that the string that follows `mail exchange = ` matches one of the following values: 

      For the US East \(N\. Virginia\) Region, the record must be: `10 inbound-smtp.us-east-1.amazonaws.com`

      For the EU \(Ireland\) Region, the record must be: `10 inbound-smtp.eu-west-1.amazonaws.com`

      For the US West \(Oregon\) Region, the record must be: `10 inbound-smtp.us-west-2.amazonaws.com`
**Note**  
`10` represents the MX preference number or priority\.

## Common Domain Verification Problems<a name="domain-verification-issues"></a>

If you have any issues with domain verification, see the list below for possible solutions\.
+ **Your DNS provider does not allow underscores in TXT record names** — You can omit `_amazonses` from the TXT record name\.
+ **You want to verify the same domain multiple times and you can't have multiple TXT records with the same name** — You might need to verify your domain more than one time because you're sending in different regions or you're sending from multiple AWS accounts from the same domain in the same region\. If your DNS provider does not allow you to have multiple TXT records with the same name, there are two workarounds\. The first workaround, if your DNS provider allows it, is to assign multiple values to the TXT record\. For example, if your DNS is managed by Amazon Route 53, you can set up multiple values for the same TXT record as follows:

  1. In the Amazon Route 53 console, choose the `_amazonses` TXT record that you added when you verified your domain in the first region\.

  1. For **Value**, press **Enter** after the first value\.

  1. Add the value for the additional region, and save the record set\.

  If you only need to verify your domain twice, another workaround you can try is to verify it one time with `_amazonses` in the TXT record name and then omit `_amazonses` from the record name entirely\. We recommend the multiple value solution as a best practice\.
+ **Amazon WorkMail reports that domain verification failed**— The domain displays a status of "failed" in the **Domains** tab of the Amazon WorkMail console\. This means that Amazon WorkMail cannot find the necessary TXT record on your DNS server\. Verify that the required TXT record is correctly published to your DNS server by using the procedure in [How to Check Domain Verification Settings](#domain-verification-check-dns), and look for the following possible error\.
  + **Your DNS provider appended the domain name to the end of the TXT record**—Adding a TXT record that already contains the domain name \(such as \_amazonses\.example\.com\) may result in the duplication of the domain name \(such as \_amazonses\.example\.com\.example\.com\)\. To avoid duplication of the domain name, add a period to the end of the domain name in the TXT record\. This indicates to your DNS provider that the record name is fully qualified \(that is, no longer relative to the domain name\), and prevents the DNS provider from appending an additional domain name\.