# Managing Email Flows<a name="email-flows"></a>

You can set up *email flow rules* for handling incoming email based on a sender's email address or domain\. These flow rules help prevent email from undesirable senders reaching your users' mailboxes\. Unlike email rules for individual mailboxes, email flow rules automatically apply to all email sent to anyone inside the Amazon WorkMail organization\.

To create an email flow rule, you specify a [*rule action*](#email-flows-rule-actions) to apply to an email when a specified [*sender pattern*](#email-flows-patterns) is matched\.


+ [Rule Actions](#email-flows-rule-actions)
+ [Sender Patterns](#email-flows-patterns)
+ [Creating an Email Flow Rule](create-email-rules.md)
+ [Testing an Email Flow Rule](test-email-flow-rule.md)
+ [Modifying an Email Flow Rule](modify-email-flow-rule.md)
+ [Removing an Email Flow Rule](remove-email-flow-rule.md)

## Rule Actions<a name="email-flows-rule-actions"></a>

Email flow rules define how incoming email is handled\. For each rule, you specify [sender patterns](#email-flows-patterns) together with one of the following actions\.


****  

| Action | Description | 
| --- | --- | 
|  Drop  |  The email is ignored\. It is not delivered, and the sender is not notified of the non\-delivery\.  | 
|  Bounce  |  The email is not delivered, and the sender is notified of the non\-delivery using a bounce message\.  | 
| Deliver to junk folder |  The email is delivered to users' spam folders, even if it is not originally detected to be spam by the Amazon WorkMail spam detection system\.   | 
|  Default  |  The email is delivered according to detection by the Amazon WorkMail spam detection system\. If it is detected as spam, it's delivered to the junk folder\. Otherwise, it's delivered to the inbox\. All other less specific email flow rules are ignored\. This action can be used to add exceptions to domain\-based rules by configuring it with a more specific sender pattern\. For more information, see [Sender Patterns](#email-flows-patterns)\.  | 
|  Never deliver to junk folder  |  The email is always delivered to users' inboxes, even if it is marked as spam by the Amazon WorkMail spam detection system\. Bypassing the default spam detection system could expose your users to high\-risk content from the addresses that you specify\.  | 

**Note**  
Incoming mail is first delivered to Amazon SES and then to Amazon WorkMail\. If an incoming email is dropped by Amazon SES \(for example, when a known virus is detected or because of explicit IP filtering rules\), specifying a delivery action \(for example, **Default**, **Deliver to junk folder**, or **Never deliver to junk folder**\) has no effect\.

## Sender Patterns<a name="email-flows-patterns"></a>

An email flow rule can apply to a specific email address, or all email addresses under a specific domain or set of domains\. You define a sender pattern to determine the email addresses to which a rule applies\.

A sender pattern can take one of the following forms:

+ **An email address** matches a single email address; for example:

  ```
  mailbox@domain.com
  ```

+ **A domain name** matches all email addresses under that domain; for example:

  ```
  domain.com
  ```

+ **A wildcard domain** matches all email addresses under that domain and all of its subdomains\. A wildcard can only appear at the front of a domain; for example:

  ```
  *.domain.com
  ```

+ **Star** matches any email addresses under any domain\.

  ```
  *
  ```

Multiple patterns can be specified for one rule\. For more information, see [Rule Actions](#email-flows-rule-actions)\. If either the `Sender` or `From` header in an incoming email matches any patterns, an email flow rule is applied\. If present, the `Sender` address is matched first\. The `From` address is matched if there is no `Sender` header or if the `Sender` header doesn't match any rule\.

If multiple rules match, the action of the most specific rule is applied; for example, a rule for a specific email address takes precedence over a rule for an entire domain\. If multiple rules have the same specificity, the most restrictive action is applied; for example, a **Drop** action takes precedence over a **Bounce** action\. The order of precedence for actions is the same as the order in which they are listed in [Rule Actions](#email-flows-rule-actions)\.

**Note**  
Take care when creating rules with overlapping sender patterns with **Drop** or **Bounce** actions\. Unexpected precedence ordering could result in chunks of incoming email not being delivered\.