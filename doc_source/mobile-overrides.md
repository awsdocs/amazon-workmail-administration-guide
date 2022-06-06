# Managing mobile device access overrides<a name="mobile-overrides"></a>

You use mobile device access overrides to override the results of mobile device access rules\. The overrides apply to specific users and devices, and it reverses the default access rule\. You can also use overrides to create one\-off exceptions to access rules and allow or deny specific user and device pairs\. In addition, you can use overrides with a `DefaultDenyAll` mobile device access rule\. That defers access decisions to a third\-party mobile device management \(MDM\) solution\. For more information, see [Managing overrides](#managing-overrides) and [Integrating with mobile device management solutions](mdm-integration.md) 

**Topics**
+ [How mobile device access overrides work](#how-overrides-work)
+ [Managing overrides](#managing-overrides)

## How mobile device access overrides work<a name="how-overrides-work"></a>

You create mobile device access overrides for a specific user and device pair\. The override reverses the default access result when evaluating mobile device access rules for a given user and device\. For example, if an access rule normally denies access, an access override allows that user and device to synchronize their email\. Conversely, if an access rule normally allows access, you can create an override that prevents the user and device from synchronizing their mail\. When you delete a mobile device access override, Amazon WorkMail again respects the result of the current mobile device access rules when deciding whether to grant access for that user and device\.

**Important**  
When you change a mobile device access override for an Amazon WorkMail organization, the affected devices can take five minutes to follow the updated override\.

## Managing overrides<a name="managing-overrides"></a>

Mobile device access overrides can be created, updated, or deleted using the API or AWS Command Line Interface\. For more information about the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)\.

To find device ID, use the AWS Management Console\. For more information, see [Viewing mobile device details](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-devices.html#view_device_details)\.

**Listing mobile device access overrides**  
This example shows how to list all mobile device access overrides for a specified Amazon WorkMail organization\.

```
aws workmail list-mobile-device-access-overrides --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56
```

**Creating and updating mobile device access overrides**  
This will create a mobile device access override to deny access to the specified Amazon WorkMail organization, user, and device ID\.

```
aws workmail put-mobile-device-access-override --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --user-id user1@domain.com --device-id 6APMEKPHCP2ND42VIJ4BR8ECDO --effect DENY
```

An existing mobile device access override can be modified to have a different effect\. This will update the previously created mobile device access override to allow access instead of denying\.

```
aws workmail put-mobile-device-access-override --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --user-id user1@domain.com --device-id 6APMEKPHCP2ND42VIJ4BR8ECDO --effect ALLOW
```

**Deleting mobile device access overrides**  
This will delete the mobile device access override for the specified Amazon WorkMail organization, user, and device ID\.

```
aws workmail delete-mobile-device-access-override --organization-id m-a123b4c5de678fg9h0ij1k2lm234no56 --user-id user1@domain.com --device-id 6APMEKPHCP2ND42VIJ4BR8ECDO
```