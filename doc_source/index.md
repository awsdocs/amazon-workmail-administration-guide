# Amazon WorkMail Administrator Guide

-----
*****Copyright &copy; 2019 Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in 
     connection with any product or service that is not Amazon's, 
     in any manner that is likely to cause confusion among customers, 
     or in any manner that disparages or discredits Amazon. All other 
     trademarks not owned by Amazon are the property of their respective
     owners, who may or may not be affiliated with, connected to, or 
     sponsored by Amazon.

-----
## Contents
+ [What Is Amazon WorkMail?](what_is.md)
+ [Prerequisites](prereqs.md)
+ [Security in Amazon WorkMail](security.md)
   + [Identity and Access Management for Amazon WorkMail](security-iam.md)
      + [How Amazon WorkMail Works with IAM](security_iam_service-with-iam.md)
      + [Amazon WorkMail Identity-Based Policy Examples](security_iam_id-based-policy-examples.md)
      + [Troubleshooting Amazon WorkMail Identity and Access](security_iam_troubleshoot.md)
   + [Using Service-Linked Roles for Amazon WorkMail](using-service-linked-roles.md)
   + [Logging and Monitoring in Amazon WorkMail](monitoring-overview.md)
      + [Monitoring Amazon WorkMail with Amazon CloudWatch](monitoring-workmail-cloudwatch.md)
      + [Logging Amazon WorkMail API Calls with AWS CloudTrail](logging-using-cloudtrail.md)
   + [Compliance Validation for Amazon WorkMail](compliance.md)
   + [Resilience in Amazon WorkMail](disaster-recovery-resiliency.md)
   + [Infrastructure Security in Amazon WorkMail](infrastructure-security.md)
+ [Getting Started With Amazon WorkMail](getting_started.md)
   + [Getting Started with Amazon WorkMail](howto-start.md)
   + [Migrating to Amazon WorkMail](migration_overview.md)
   + [Interoperability Between Amazon WorkMail and Microsoft Exchange](interoperability.md)
      + [Enable Email Routing Between Microsoft Exchange and Amazon WorkMail Users](setup-msexchange.md)
      + [Configure Availability Settings on Amazon WorkMail](enable_interop_wm.md)
      + [Configure Availability Settings in Microsoft Exchange](enable_interop_ms.md)
      + [Disabling Interoperability and Decommissioning Your Mail Server](disable_interop.md)
      + [Troubleshooting](troubleshooting_interop.md)
   + [Amazon WorkMail Limits](workmail_limits.md)
+ [Working with Organizations](organizations_overview.md)
   + [Adding an Organization](add_new_organization.md)
   + [Removing an Organization](remove_organization.md)
   + [Editing Your Organization's Mobile Device Policy](edit_organization_mobile_policy.md)
   + [Managing Email Flows](email-flows.md)
      + [Creating an Email Flow Rule](create-email-rules.md)
      + [Configuring SMTP Gateways](smtp-gateway.md)
      + [Configuring AWS Lambda for Amazon WorkMail](lambda.md)
      + [Retrieving Message Content with AWS Lambda](lambda-content.md)
      + [Testing an Email Flow Rule](test-email-flow-rule.md)
      + [Modifying an Email Flow Rule](modify-email-flow-rule.md)
      + [Removing an Email Flow Rule](remove-email-flow-rule.md)
   + [Tracking Messages](tracking.md)
   + [Enforcing DMARC Policies on Incoming Email](inbound-dmarc.md)
+ [Working with Domains](domains_overview.md)
   + [Adding a Domain](add_domain.md)
   + [Removing a Domain](remove_domain.md)
   + [Choosing the Default Domain](default_domain.md)
   + [Verifying Domains](domain_verification.md)
   + [Enabling AutoDiscover to Configure Endpoints](autodiscover.md)
   + [Editing Domain Identity Policies](editing_domains.md)
   + [Authenticating Email with SPF](authenticate_domain.md)
+ [Working with Users](users_overview.md)
   + [Managing User Accounts](manage-users.md)
   + [Managing User Mailboxes](manage-mailboxes.md)
   + [Managing Mobile Devices](manage-devices.md)
   + [Enabling Signed or Encrypted Email](enable_encryption.md)
+ [Working with Groups](groups_overview.md)
   + [Create a Group](add_new_group.md)
   + [Enable an Existing Group](enable_existing_group.md)
   + [Add Users to a Group](add-group-users.md)
   + [Remove Users from a Group](remove-group-users.md)
   + [Disable a Group](remove_group.md)
+ [Working with Mailbox Permissions](mail_perms_overview.md)
+ [Working with Resources](resources_overview.md)
   + [Creating a Resource](create_resource.md)
   + [Editing a Resource](edit_resource.md)
   + [Removing a Resource](remove_resource.md)
+ [Using Email Journaling with Amazon WorkMail](journaling_overview.md)
+ [Document History](DocumentHistory.md)