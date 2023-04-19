# Programmatic access to mailboxes<a name="mail_perms_programmatic"></a>

To programmatically access Amazon WorkMail mailboxes, use the Exchange Web Services \(EWS\) protocol\. With EWS, you can access all item types in a mailbox\. Here are some EWS libraries that you can use with Amazon WorkMail: 
+ **Java** – [EWS Java API](https://github.com/OfficeDev/ews-java-api)
+ **\.Net** – [EWS Managed API](https://github.com/OfficeDev/ews-managed-api)
+ **Python** – [Exchangelib](https://pypi.org/project/exchangelib/)

Amazon WorkMail also supports IMAP and SMTP protocols, which you can use to send and receive emails\. You can see the URLs supported for Amazon WorkMail protocols under [Amazon WorkMail endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/workmail.html)\.

When using the EWS protocol, Amazon WorkMail supports the following authentication methods:
+ **Basic Authentication** – With basic authentication, you enter an email address and password\. 
+ **Impersonation roles** – With impersonation roles, you access users' mailboxes without entering the user's credentials\.

**Topics**
+ [Managing impersonation roles](managing-impersonation-roles.md)
+ [Using impersonation roles](using-impersonation-roles.md)