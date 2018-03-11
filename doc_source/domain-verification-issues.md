# Common Domain Verification Problems<a name="domain-verification-issues"></a>

If you have any issues with domain verification, see the list below for possible solutions\.

+ **Your DNS provider does not allow underscores in TXT record names** — You can omit `_amazonses` from the TXT record name\.

+ **You want to verify the same domain multiple times and you can't have multiple TXT records with the same name** — You might need to verify your domain more than one time because you're sending in different regions or you're sending from multiple AWS accounts from the same domain in the same region\. If your DNS provider does not allow you to have multiple TXT records with the same name, there are two workarounds\. The first workaround, if your DNS provider allows it, is to assign multiple values to the TXT record\. For example, if your DNS is managed by Amazon Route 53, you can set up multiple values for the same TXT record as follows:

  1. In the Amazon Route 53 console, choose the `_amazonses` TXT record that you added when you verified your domain in the first region\.

  1. For **Value**, press **Enter** after the first value\.

  1. Add the value for the additional region, and save the record set\.

  If you only need to verify your domain twice, another workaround you can try is to verify it one time with `_amazonses` in the TXT record name and then omit `_amazonses` from the record name entirely\. We recommend the multiple value solution as a best practice\.

+ **Amazon WorkMail reports that domain verification failed**— The domain displays a status of "failed" in the **Domains** tab of the Amazon WorkMail console\. This means that Amazon WorkMail cannot find the necessary TXT record on your DNS server\. Verify that the required TXT record is correctly published to your DNS server by using the procedure in [How to Check Domain Verification Settings](domain-verification-check-dns.md), and look for the following possible error\.

+ **Your DNS provider appended the domain name to the end of the TXT record**—Adding a TXT record that already contains the domain name \(such as \_amazonses\.example\.com\) may result in the duplication of the domain name \(such as \_amazonses\.example\.com\.example\.com\)\. To avoid duplication of the domain name, add a period to the end of the domain name in the TXT record\. This indicates to your DNS provider that the record name is fully qualified \(that is, no longer relative to the domain name\), and prevents the DNS provider from appending an additional domain name\.