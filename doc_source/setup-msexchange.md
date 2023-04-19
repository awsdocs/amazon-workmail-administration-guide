# Enable email routing between Microsoft Exchange and Amazon WorkMail users<a name="setup-msexchange"></a>

With email routing between Microsoft Exchange Server and Amazon WorkMail, users can keep their existing email addresses after they migrate to Amazon WorkMail\. Email routing lets you keep Microsoft Exchange Server as the primary Simple Mail Transfer Protocol \(SMTP\) server for incoming email for your organization\.

Before using email routing, you'll need to complete the following prerequisites:
+ Enable interoperability mode for your organization\. For more information, see [Enable interoperability](interoperability.md#enable_interoperability)\.
+ Ensure that you see your domain in the Amazon WorkMail console\.
+ Verify that our Microsoft Exchange Server can send email to the internet\. You might need to configure a Send connector\. For more information about Send connectors, see [ Create a Send connector in Exchange Server to send mail to the internet ](https://docs.microsoft.com/en-us/exchange/mail-flow/connectors/internet-mail-send-connectors?view=exchserver-2019) in the Microsoft documentation\.