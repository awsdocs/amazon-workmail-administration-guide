# Integrating with mobile device management solutions<a name="mdm-integration"></a>

Amazon WorkMail supports some basic mobile device management capabilities through mobile device policies and mobile device access rules\. However, those features can only interact with mobile devices through the Microsoft Exchange ActiveSync \(EAS\) protocol, so they have limited ability to introspect and enforce device security posture\. Administrators who need greater control over device security and compliance can use a third\-party mobile device management \(MDM\) solution\.

## Mobile device management solutions overview<a name="mdm-overview"></a>

You can configure your MDM solution in two modes, *proxy* or *direct*\. Consult your MDM documentation to see which modes your solution supports\.

In proxy mode, mobile devices use the Exchange Active Sync \(EAS\) protocol via your MDM solution to access Amazon WorkMail\. The MDM solution uses device posture to allow or deny access to Amazon WorkMail data\. On the Amazon WorkMail side, use an Access Control Rule that allows EAS access only from the MDM solution's IP address or addresses\. For more information, refer to [Working with access control rules](https://docs.aws.amazon.com/workmail/latest/adminguide/access-rules.html)\.

The following image shows a typical proxy mode configuration\.

![\[\]](http://docs.aws.amazon.com/workmail/latest/adminguide/images/mdm-proxy.png)

In direct mode, mobile devices use EAS to access Amazon WorkMail directly\. Your MDM solution receives device posture changes and continually assesses whether each device meets those requirements\. When the MDM solution detects a posture changes, such as a device going out of compliance, it can take several actions and typically emits notifications or events\. An Amazon WorkMail administrator can set up a system to listen to these compliance status events and automatically create mobile device access overrides that allow or deny access to devices when they go in or out of compliance with the MDM device requirements\. 

The following image shows a typical direct mode configuration\.

![\[\]](http://docs.aws.amazon.com/workmail/latest/adminguide/images/mdm-direct.png)

## Configuring a WorkMail organization to integrate with a third\-party MDM solution in direct mode<a name="configure-mdm"></a>

To integrate with a third\-party mobile device management \(MDM\) solution in direct mode, you must meet these requirements:
+ Create access control rules that restrict access to user devices to only the ActiveSync protocol\.
+ Create a default "deny\-to\-all" mobile device access rule to ensure that all unknown or unmanaged mobile devices are denied by default\.
+ Adopt a mobile device management solution that emits custom notifications or events when a device changes security posture, meaning it goes in or out of compliance\.
+ Create a custom software component to listen to those notifications and call the Amazon WorkMail SDK to create mobile device access overrides\.

These components ensure that all user devices meet their MDM compliance requirements before being allowed to access their Amazon WorkMail mailboxes\.

**Use access control rules to restrict mobile device access to ActiveSync**  
You must ensure that all devices use only the ActiveSync protocol, and you can use access control rules to do so\. For example, you can grant access to other mail protocols only from an internal corporate IP address range, and then allow only ActiveSync when accessing eamil from outside the corporate firewall\. You must do this because only ActiveSync allows you to identify devices using a device ID\. You can't use protocols such as the Internet Message Access Protocol \(IMAP\) or Exchange Web Services\. For more information, see [Working with access control rules](access-rules.md)\. 

**Create a default 'deny to all' access rule**  
To defer all mobile device access decisions to the third\-party mobile device management solution, create an access rule that automatically denies all devices unless overridden on a per\-user or per\-device basis\. For more information, refer to [Managing mobile device access rules](manage-mobile-access.md)\.

This example shows a 'deny to all' rule\.

```
aws workmail create-mobile-device-access-rule --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --name DefaultDenyAll --effect DENY
```

**React to device posture changes and create mobile device access overrides**  
You must configure your MDM solution to send notifications for device posture changes\. These notifications must be consumed by a component that can use the Amazon WorkMail SDK to create or update mobile device access overrides\. By default, Amazon WorkMail denies access to unmanaged or newly provisioned devices because of the default “deny to all” mobile device access rule shown earlier in this topic\. When the MDM solution determines that the device meets all requirements and emits a notification indicating that the device is compliant, this component can react to this notification by creating a mobile device access override with an effect of `ALLOW` for the specified user and device\. If the device later goes out of compliance, the mobile device management solution emits another notification, and the access override can be deleted or modified to deny access for that device\. For more information, see [Managing mobile device access overrides](mobile-overrides.md)\.

For an example of Amazon WorkMail integrated with MDM, see this [AWS sample application](https://github.com/aws-samples/amazon-workmail-lambda-templates/tree/master/workmail-ws1-integration)\.