# What Is Amazon WorkMail?<a name="what_is"></a>

Amazon WorkMail is a secure, managed business email and calendaring service with support for existing desktop and mobile email clients\. You can access your email, contacts, and calendars using Microsoft Outlook, your browser, or their native iOS and Android email applications\. You can integrate Amazon WorkMail with your existing corporate directory and control both the keys that encrypt your data and the location in which your data is stored\.


+ [Amazon WorkMail Concepts](#workmail_concepts)
+ [Accessing Amazon WorkMail](#accessing_workmail)
+ [Amazon WorkMail Pricing](#workmail_pricing)
+ [Regions and Endpoints](#regions_endpoints)
+ [Amazon WorkMail Limits](#workmail_limits)
+ [Related AWS Services](#related_services)
+ [Amazon WorkMail Resources](#RelatedResources)

## Amazon WorkMail Concepts<a name="workmail_concepts"></a>

The terminology and concepts that are central to your understanding and use of Amazon WorkMail are described below\.

**Organization**  
A tenant setup for Amazon WorkMail\.

**Alias**  
A globally unique name to identify your organization\. The alias is used to access the Amazon WorkMail web application \(https://**youralias**\.awsapps\.com/mail\)\.

**Domain**  
The web address that comes after the @ symbol in an email address\. You can add a domain that receives mail and delivers it to mailboxes in your organization\.

**Test mail domain**  
A domain is automatically configured during setup that can be used for testing Amazon WorkMail\. The test mail domain is **youralias**\.awsapps\.com and is used as the default domain if you do not configure your own domain\. The test mail domain is subject to different limits\. For more information, see [Amazon WorkMail Organization and User Limits](#user_limits)\.

**Directory**  
An AWS Simple AD, AWS Managed AD, or AD Connector created in AWS Directory Service\. If you create an organization using the Amazon WorkMail Quick setup, we create a WorkMail directory for you\. You cannot view a WorkMail directory in AWS Directory Service\.

**User**  
A user created in the AWS Directory Service and enabled for Amazon WorkMail\.

**Group**  
A group used in AWS Directory Service used as distribution list or security group in Amazon WorkMail\.

**Mobile device policy**  
Various IT policy rules that control the security features and behavior of a mobile device\.

## Accessing Amazon WorkMail<a name="accessing_workmail"></a>

Amazon WorkMail works with all major mobile devices and operating systems that support the Exchange ActiveSync protocol, including the Apple iPad, Apple iPhone, Amazon Kindle Fire, Android, Windows Phone, and BlackBerry 10\.

You can access Amazon WorkMail from Microsoft Outlook on Windows\. You must have a valid Microsoft Outlook license to use it with Amazon WorkMail, which offers native support for the following versions:

+ Microsoft Outlook 2007, 2010, 2013, and 2016

+ Microsoft Outlook 2010 and 2013 Click\-to\-Run

+ Microsoft Outlook for Mac 2011

+ Microsoft Outlook 2016 for Mac

Amazon WorkMail supports IMAP clients\. For the required configuration, see [Connect to your IMAP Client Application](http://docs.aws.amazon.com/workmail/latest/userguide/using_IMAP_client.html)\. POP3 clients are not currently supported\.

You can access Amazon WorkMail using the web application: https://**alias**\.awsapps\.com/mail\.

## Amazon WorkMail Pricing<a name="workmail_pricing"></a>

With Amazon WorkMail, there are no upfront fees or commitments\. You pay only for active user accounts\. For more specific information about pricing, see [Pricing](http://aws.amazon.com/workmail/pricing)\.

## Regions and Endpoints<a name="regions_endpoints"></a>

For a list of supported regions and endpoints, see [AWS Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html#wm_region)\.

## Amazon WorkMail Limits<a name="workmail_limits"></a>

Amazon WorkMail can be used by enterprise customers as well as small business owners\. Although we support most use cases without the need to configure any changes in limits, we also protect our users and the internet against abuse of the product\. Therefore, some customers may run into limits that we have set\. This section describes these limits and how to change them\.

Some limit values can be changed, and some are hard limits that cannot be changed\. If you want to change a limit value for Amazon WorkMail, follow these steps to submit a limit increase request:

1. Go to the AWS Support Center, sign in if prompted, and then choose **Create Case**\.

1. Under **Regarding**, choose **Service Limit Increase**\.

1. Under **Limit Type**, choose the type of limit to increase, fill in the necessary form fields, and then choose your preferred method of contact\.

1. If you are requesting a limit increase for a specific organization, enter the **Organization Alias**\.

1. Wait up to five working days for increases to become effective\.

**Note**  
It is possible to request a limit increase regardless of the age of the account\. When you create a new AWS account, the values you are subjected to are usually lower than those for veteran accounts\. On this page, only the default limit values for veteran accounts are listed\.

### Amazon WorkMail Organization and User Limits<a name="user_limits"></a>

You can add up to 25 users for a 30\-day free trial\. After this period ends, you are charged for all active users unless you remove them or close your Amazon WorkMail account\.

All messages that are sent to another user are considered when evaluating these limits\. These include emails, meeting requests, meeting responses, task requests, and messages that are forwarded or redirected automatically as the result of a rule\.

**Note**  
When requesting a limit increase request only for a specific organization, include the organization name in your request\.


| Resource | Default Limit  | Upper Bound for Change Requests  | 
| --- | --- | --- | 
|  Users per Amazon WorkMail organization  |  1,000  |  Can be increased depending on the directory type that is used for the organization: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/workmail/latest/adminguide/what_is.html) \*If you are using Simple AD or AD Connector, see [AWS Directory Service](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/what_is.html) for additional information\.  | 
| Free trial users |  Up to 25 users in the first 30 days  |  The free trial period is only applicable for the first 25 users in any organization\. Any additional users are not included in the free trial offer\.  | 
| Recipients addressed per AWS account per day  | 100,000 recipients external to the organization, with no hard limit on recipients internal to the organization | There is no upper bound\. However, Amazon WorkMail is a business email service and not intended to be used for bulk email services\. For bulk email services, see [Amazon SES](https://aws.amazon.com/ses/) or [Amazon Pinpoint](https://aws.amazon.com/pinpoint/)\. | 
| Recipients addressed per AWS account per day using any of the test domains | 200 recipients, regardless of destination | There is no upper bound\. However, the test mail domain is not intended for long\-term usage\. Instead, we recommend that you add your own domain and use it as the default domain\. | 

### WorkMail Organization Setting Limits<a name="organization_limits"></a>


| Resource | Default Limit | 
| --- | --- | 
| Number of domains per Amazon WorkMail organization | 1,000This is a hard limit and cannot be changed\.  | 
|  Number of sender patterns in email flow rules per organization  |  250 This is a hard limit and cannot be changed\.  | 

### Per\-User Limits<a name="per_user_limits"></a>

All messages that are sent to another user are considered when evaluating these limits\. These include emails, meeting requests, meeting responses, task requests, and messages that are forwarded or redirected automatically as the result of a rule\.


| Resource | Default Limit | Upper Limit for Change Requests | 
| --- | --- | --- | 
| Maximum size of mailbox | 50 GB |  50 GB  | 
| Maximum number of aliases per user |  100 This is a hard limit and cannot be changed\.  |  N/A  | 
| Recipients addressed per user per day using the domain that you own | 10,000 recipients external to the organization, with no hard limit on recipients internal to the organization\. | There is no upper bound\. However, Amazon WorkMail is a business email service and not intended to be used for bulk email services\. For bulk email services, see [Amazon SES](https://aws.amazon.com/ses/) or [Amazon Pinpoint](https://aws.amazon.com/pinpoint/)\. | 

### Message Limits<a name="message_limits"></a>

All messages that are sent to another user are considered when evaluating these limits\. These include emails, meeting requests, meeting responses, task requests, and messages that are forwarded or redirected automatically as the result of a rule\.


| Resource  | Default Limit  | 
| --- | --- | 
|  Maximum size of incoming message  | 25 MBThis is a hard limit and cannot be changed\. | 
| Maximum size of outgoing message | 25 MBThis is a hard limit and cannot be changed\. | 
|  Number of recipients per message  | 500This is a hard limit and cannot be changed\. | 

## Related AWS Services<a name="related_services"></a>

The following services are used along with Amazon WorkMail:

+ **AWS Directory Service**—You can integrate Amazon WorkMail with an existing AWS Simple AD, AWS Managed AD, or AD Connector\. Create a directory in the AWS Directory Service and then enable Amazon WorkMail for this directory\. After you've configured this integration, you can choose which users you would like to enable for Amazon WorkMail from a list of users in your existing directory, and users can log in using their existing Active Directory credentials\. For more information, see [AWS Directory Service Administration Guide](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/)\.

+ **Amazon Simple Email Service**—Amazon WorkMail uses Amazon SES to send all outgoing email\. The test mail domain and your domains are available for management in the Amazon SES console\. There is no cost for outgoing email sent from Amazon WorkMail\. For more information, see [Amazon Simple Email Service Developer Guide](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/)\.

+ **AWS Identity and Access Management**—The AWS Management Console requires your user name and password so that any service you use can determine whether you have permission to access its resources\. We recommend that you avoid using AWS account credentials to access AWS because AWS account credentials cannot be revoked or limited in any way\. Instead, we recommend that you create an IAM user and add the user to an IAM group with administrative permissions\. You can then access the console using the IAM user credentials\.

  If you signed up for AWS but have not created an IAM user for yourself, you can create one using the IAM console\. For more information, see [Create Individual IAM Users](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPractices.html#create-iam-users) in the *IAM User Guide*\.

+ **AWS Key Management Service**—Amazon WorkMail is integrated with AWS KMS for encryption of customer data\. Key management can be performed from the AWS KMS console\. For more information, see [What is the AWS Key Management Service](http://docs.aws.amazon.com/kms/latest/developerguide/overview.html) in the *AWS Key Management Service Developer Guide*\.

## Amazon WorkMail Resources<a name="RelatedResources"></a>

The following related resources can help you as you work with this service\.

+ ** [Classes & Workshops](https://aws.amazon.com/training/course-descriptions/)** – Links to role\-based and specialty courses as well as self\-paced labs to help sharpen your AWS skills and gain practical experience\.

+ ** [AWS Developer Tools](https://aws.amazon.com/tools/)** – Links to developer tools, SDKs, IDE toolkits, and command line tools for developing and managing AWS applications\.

+ ** [AWS Whitepapers](https://aws.amazon.com/whitepapers/)** – Links to a comprehensive list of technical AWS whitepapers, covering topics such as architecture, security, and economics and authored by AWS Solutions Architects or other technical experts\.

+ ** [AWS Support Center](https://console.aws.amazon.com/support/home#/)** – The hub for creating and managing your AWS Support cases\. Also includes links to other helpful resources, such as forums, technical FAQs, service health status, and AWS Trusted Advisor\.

+ ** [AWS Support](https://aws.amazon.com/premiumsupport/)** – The primary web page for information about AWS Support, a one\-on\-one, fast\-response support channel to help you build and run applications in the cloud\.

+ ** [Contact Us](https://aws.amazon.com/contact-us/)** – A central contact point for inquiries concerning AWS billing, account, events, abuse, and other issues\. 

+ ** [AWS Site Terms](https://aws.amazon.com/terms/)** – Detailed information about our copyright and trademark; your account, license, and site access; and other topics\.