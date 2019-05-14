# Managing Email Flows<a name="email-flows"></a>

You can set up *email flow rules* to handle email flows based on email addresses or domains\. Inbound email flow rules are based on the sender's email address or domain\. Outbound email flow rules are based on both the sender's and recipient's email addresses or domains\.

To create an email flow rule, specify a [*rule action*](#email-flows-rule-actions) to apply to an email when a specified [*pattern*](#email-flows-patterns) is matched\.

**Topics**
+ [Inbound Email Rule Actions](#email-flows-rule-actions)
+ [Outbound Email Rule Actions](#email-flows-rule-outbound)
+ [Sender and Recipient Patterns](#email-flows-patterns)
+ [Creating an Email Flow Rule](create-email-rules.md)
+ [Configuring SMTP Gateways](smtp-gateway.md)
+ [Configuring AWS Lambda for Amazon WorkMail](lambda.md)
+ [Testing an Email Flow Rule](test-email-flow-rule.md)
+ [Modifying an Email Flow Rule](modify-email-flow-rule.md)
+ [Removing an Email Flow Rule](remove-email-flow-rule.md)

## Inbound Email Rule Actions<a name="email-flows-rule-actions"></a>

Inbound email flow rules help prevent undesirable email from reaching your users' mailboxes\. You can use these rules with an AWS Lambda function to process incoming email before it is delivered to your users' mailboxes\. For more information about using Lambda with Amazon WorkMail, see [Configuring Lambda for Amazon WorkMail](lambda.md)\. For more information about Lambda, see the [https://docs.aws.amazon.com/lambda/latest/dg/welcome.html](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)\.

Unlike email rules for individual mailboxes, inbound email flow rules, also called rule actions, automatically apply to all email sent to anyone inside the Amazon WorkMail organization\.

The following rule actions define how inbound email is handled\. For each rule, you specify [sender patterns](#email-flows-patterns) together with one of the following actions\. 


****  

| Action | Description | 
| --- | --- | 
|  Drop  |  The email is ignored\. It is not delivered, and the sender is not notified of the non\-delivery\.  | 
|  Bounce  |  The email is not delivered, and the sender is notified of the non\-delivery in a bounce message\.  | 
| Deliver to junk folder |  The email is delivered to users' spam or junk folders, even if it is not originally identified as spam by the Amazon WorkMail spam detection system\.   | 
|  Default  |  The email is delivered after being checked by the Amazon WorkMail spam detection system\. Spam email is delivered to the junk folder\. All other emails are delivered to the inbox\. Other email flow rules with a less specific sender pattern are ignored\. To add exceptions to domain\-based email flow rules, configure the Default action with a more specific sender pattern\. For more information, see [Sender and Recipient Patterns](#email-flows-patterns)\.  | 
|  Never deliver to junk folder  |  The email is always delivered to users' inboxes, even if it is identified as spam by the Amazon WorkMail spam detection system\. By not using the default spam detection system, you could expose your users to high\-risk content from the addresses that you specify\.  | 
|  Run Lambda  |  Passes the email to a Lambda function for processing before it is delivered to users' inboxes\.  | 

**Note**  
Inbound email is first delivered to Amazon SES and then to Amazon WorkMail\. If Amazon SES blocks an incoming email, then rule actions won't apply\. For example, Amazon SES blocks an email when a known virus is detected or because of explicit IP filtering rules\. Specifying a rule action, such as **Default**, **Deliver to junk folder**, or **Never deliver to junk folder** has no effect\.

## Outbound Email Rule Actions<a name="email-flows-rule-outbound"></a>

Outbound email flow rules can be used to direct emails via SMTP gateways, or to block senders from sending emails to specified recipients\. For more information on SMTP gateways, see [Configuring SMTP Gateways](smtp-gateway.md)\.

Outbound email flow rules can also be used to pass the email to an AWS Lambda function for processing after the email is sent\. For more information about using Lambda with Amazon WorkMail, see [Configuring Lambda for Amazon WorkMail](lambda.md)\. For more information about Lambda, see the [https://docs.aws.amazon.com/lambda/latest/dg/welcome.html](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)\.

The following rule actions define how outbound email is handled\. For each rule, you specify [sender and recipient patterns](#email-flows-patterns) together with one of the following actions\. 


****  

| Action | Description | 
| --- | --- | 
|  Default  |  The email is sent via the normal flow\.  | 
|  Drop  |  The email is dropped\. It is not sent, and the sender is not notified\.  | 
| Bounce to sender |  The email is not sent, and the sender is notified with a message that the administrator blocked the email\.   | 
|  Route to SMTP gateway  |  The email is sent via a configured SMTP gateway\.  | 
|  Run Lambda  |  Passes the email to a Lambda function for processing after the email is sent\. Does not affect email sending\.  | 

## Sender and Recipient Patterns<a name="email-flows-patterns"></a>

An email flow rule can apply to a specific email address, or all email addresses under a specific domain or set of domains\. You define a pattern to determine the email addresses that a rule applies to\.

Both sender and recipient patterns take one of the following forms:
+ **An email address** matches a single email address; for example:

  ```
  mailbox@example.com
  ```
+ **A domain name** matches all email addresses under that domain; for example:

  ```
  example.com
  ```
+ **A wildcard domain** matches all email addresses under that domain and all of its subdomains\. A wildcard appears only at the front of a domain; for example:

  ```
  *example.com
  ```
+ **Star** matches any email addresses under any domain\.

  ```
  *
  ```

Multiple patterns can be specified for one rule\. For more information, see [Inbound Email Rule Actions](#email-flows-rule-actions) and [Outbound Email Rule Actions](#email-flows-rule-outbound)\.

Inbound email flow rules are applied if either the `Sender` or `From` header in an inbound email matches any patterns\. If present, the `Sender` address is matched first\. The `From` address is matched if there is no `Sender` header or if the `Sender` header doesn't match any rule\.

Outbound email flow rules are applied if the recipient and either the `Sender` or `From` header in an outbound email matches any patterns\. If there are multiple recipients for the email that match different rules, each rule applies for the matched recipients\.

If multiple rules match, the action of the most specific rule is applied\. An example is when a rule for a specific email address takes precedence over a rule for an entire domain\. If multiple rules have the same specificity, the most restrictive action is applied\. An example is when a **Drop** action takes precedence over a **Bounce** action\. The order of precedence for actions is the same as the order in which they are listed in [Inbound Email Rule Actions](#email-flows-rule-actions) and [Outbound Email Rule Actions](#email-flows-rule-outbound)\.

**Note**  
Take care when creating rules with overlapping sender patterns with **Drop** or **Bounce** actions\. Unexpected precedence ordering could result in many inbound emails not being delivered\.