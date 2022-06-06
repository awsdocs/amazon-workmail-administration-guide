# Troubleshooting mail routing issues<a name="troubleshooting"></a>

If a user stops receiving emails, your Amazon WorkMail organization may be experiencing a mail routing issue\. The steps in this section explain common ways to resolve delivery and routing issues\.

**Inbound mail issues:**
+ Check the MX record for the domain associated with your Amazon WorkMail organization\. `WorkMail` should be the only entry and should have the lowest priority\. Multiple MX records can lead to the wrong service receiving messages\. For more information about MX records, see [Verifying domains](domain_verification.md)\.
+ Check the Domain\-based Message Authentication, Reporting, and Conformance \(DMARC\) settings for your organization in the Amazon WorkMail console\. DMARC records are used to protect against common attacks, such as spoofing or phishing, that can compromise a user's account credentials\. For more information about DMARC, see [Enforcing DMARC policies on incoming email](inbound-dmarc.md)\.
+ Check the Amazon Simple Email Service inbound rule\. If the rule contains actions other than Amazon WorkMail, those actions can fail and cause Amazon WorkMail to stop receiving mail\. For more information about Amazon SES rules, see [Integrate with Amazon WorkMail action](https://docs.aws.amazon.com/ses/latest/dg/receiving-email-action-workmail.html) in the *Amazon Simple Email Service Developer Guide*\.
+ Enable message tracking in Amazon WorkMail, and then check the logs for delivery problems\. For more information about message tracking, see [Enabling event logging](tracking.md)\.

**Outbound mail issues**
+ Ensure your SPF record includes Amazon SES\. Check the domains page in the Amazon WorkMail console to verify\. For more information about SPF, see [Authenticating email with SPF](authenticate_domain.md)\.
+ Ensure Amazon WorkMail has permissions to use the domain\. If not, add the domain again\. [Adding a domain](add_domain.md) in this guide provides the how\-to steps\.