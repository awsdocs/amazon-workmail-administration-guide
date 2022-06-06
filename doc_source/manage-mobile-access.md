# Managing mobile device access rules<a name="manage-mobile-access"></a>

Mobile device access rules for Amazon WorkMail allow administrators to control mailbox access for certain types of mobile devices\. By default, each Amazon WorkMail organization uses a rule that grants mailbox access to any devices, regardless of type, model, operating system, or user agent\. You can edit or replace that default rule with one of your own\. You can also add, change, and delete rules\.

**Warning**  
If you delete all the mobile device access rules for an organization, Amazon WorkMail blocks all mobile device access\.

You can create rules that allow or deny access based on the following device properties:
+ **Device type**—"iPhone", "iPad", or "Android\."
+ **Device model**—"iPhone10C1", "iPad5C1", or "HTCOneX\."
+ **Device operating system**—"iOS 12\.3\.1 16F203", or "Android 8\.1\.0\."
+ **Device user agent**—"iOS/14\.2 \(18B92\) exchangesyncd/1\.0," or "Android\-Mail/7\.7\.16\.163886392\.release\."

To view device properties on the AWS Management Console, see [Viewing mobile device details](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-devices.html#view_device_details )\. 

**Note**  
Some devices and clients may not report properties for all fields\. For information about working around those cases, see [Dealing with empty fields](#empty-fields)

**Important**  
Amazon WorkMail mobile device access rules only apply to devices that use the Microsoft Exchange ActiveSync protocol\. Mobile clients that use a different protocol, such as IMAP, don't report the device properties listed here, so these rules won't apply\.  
If you need to restrict access for devices that use other protocols, you can create access control rules\. For more information about them, see [ Working with access control rules ](https://docs.aws.amazon.com/workmail/latest/adminguide/access-rules.html)\. As an example, you can restrict access to other protocols and webmail to just a range of corporate IP addresses, but allow Microsoft ActiveSync from elsewhere, and then use Mobile Device Access Rules to further limit the types and versions of allowed clients\.

**Topics**
+ [How mobile device access rules work](#how-rules-work)
+ [Using mobile device access rules](#use-mobile-rules)

## How mobile device access rules work<a name="how-rules-work"></a>

Mobile device access rules only apply to devices that use the Microsoft Exchange ActiveSync protocol\. Each rule has a set of conditions that specify when the rule applies, plus an access effect of `ALLOW` or `DENY` for the device\. A rule applies to an access request only if all of the conditions of the rule match properties of the user's mobile device\. Rules with no conditions apply to all requests\. Each condition uses a case\-insensitive prefix match against the device's reported properties\.

Amazon WorkMail evaluates rules as follows:
+ If any `DENY` rule matches a device property, the policy blocks the device\. `DENY` rules take precedence over `ALLOW` rules\.
+ If at least one `ALLOW` rule matches, and no `DENY` rule matches, the policy allows the device\.
+ If no rule applies, the device is blocked\.

**Important**  
Mobile devices report the properties that the rules use to operate\. The devices report their properties during the Microsoft ActiveSync device provisioning process\. Amazon WorkMail cannot independently verify that mobile clients report correct or up\-to\-date information\.

## Using mobile device access rules<a name="use-mobile-rules"></a>

You can use APIs or the AWS Command Line Interface \(CLI\) to create and manage mobile device access rules\. For more information about the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/)\. 

**Important**  
When you change an access rule for an Amazon WorkMail organization, the affected devices can take five minutes to follow the updated rule, and devices may show inconsistent behavior during that time\. However, you immediately see correct behavior when you test rules\. For more information, see [Testing mobile device access rules](#test-mobile-rule)\.

**Listing mobile device access rules**  
The following example shows how to list mobile device access rules\.

```
aws workmail list-mobile-device-access-rules --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56
```

**Creating mobile device access rules**  
The following example creates a rule that blocks all Android devices from accessing mailboxes\.

```
aws workmail create-mobile-device-access-rule --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --name BlockAllAndroid --effect DENY --device-types "android"
```

The following example creates a rule that only allows a specific version of iOS\. Be sure to remove the default `ALLOW-all` rule\.

```
aws workmail create-mobile-device-access-rule --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --name AllowLatestiOS --effect ALLOW --device-operating-systems "iOS 14.3"
```

**Updating mobile device access rules**  
The following example updates a device rule by adding an identifier\.

```
aws workmail update-mobile-device-access-rule --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --mobile-device-access-rule-id 1a2b3c4d --name AllowLatestiOS --effect ALLOW --device-operating-systems "iOS 14.4"
```

**Deleting a mobile device access rule**  
The following example deletes the mobile device access rule with the given identifier\.

```
aws workmail delete-mobile-device-access-rule --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --mobile-device-access-rule-id 1a2b3c4d
```

**Testing mobile device access rules**  
To test access rules, you can use the [GetMobileDeviceAccessEffect](https://docs.aws.amazon.com/workmail/latest/APIReference/API_GetMobileDeviceAccessEffect.html) API, or the get\-mobile\-device\-access\-effect command in the AWS CLI \. For more information about the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)\.

When you test, you pass in the properties of a simulated mobile device, and the API or CLI returns the access effect—`ALLOW` or `DENY`—that a real mobile device with those properties would receive\. For example, this command tests whether an iPhone running iOS 14\.2, plus the default mail app, can access a mailbox\.

```
aws workmail get-mobile-device-access-effect --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --device-type "iPhone" --device-model "iPhone10C1" --device-operating-system "iOS 14.2.1 16F203" --device-user-agent "iOS/14.2 (18B92) exchangesyncd/1.0"
```

**Dealing with empty fields**  
Some mobile devices or clients may not report information for one or more fields, leaving the values empty\. Rules can match against these devices by using the special value `$NONE` in a condition\. For example, a rule with `DeviceTypes=["iphone", "ipad", "$NONE"]` will match devices that report a device type of `"iphone"` or `"ipad"`, or don't report a device type at all\.

Negative conditions such as `NotDeviceTypes` or `NotDeviceUserAgents` won't match these empty values\. For example, a rule with `NotDeviceTypes=["android"]` will match devices that report a device type other than `"android"`\. However, the rule won't match devices that don't report a device type at all\.