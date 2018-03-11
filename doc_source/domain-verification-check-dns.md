# How to Check Domain Verification Settings<a name="domain-verification-check-dns"></a>

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