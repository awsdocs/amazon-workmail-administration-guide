# Managing mobile devices<a name="manage-devices"></a>

The topics in this section explain how to remotely wipe mobile devices, remove devices from your organization, and view the details for devices\. For information about editing your organization's mobile device policy, see [Editing your organization's mobile device policy](edit_mobile_policy.md)\.

**Topics**
+ [Remotely wiping mobile devices](#remote_wipe_device)
+ [Removing user devices from the devices list](#remove_mobile_device)
+ [Viewing mobile device details](#view_device_details)

## Remotely wiping mobile devices<a name="remote_wipe_device"></a>

The steps in this section explain how to remotely wipe mobile devices\. Remember the following:
+ Devices must be online and connected to Amazon WorkMail\. If someone disconnects the device, the wipe operation resumes when the user reconnects the device\.
+ Wipe operations can take five minutes to propagate\.

**Important**  
For most mobile devices, a remote wipe resets the device to factory defaults\. All data, including personal files, can be removed when you perform this procedure\.

**To remotely wipe a user's mobile device**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a region** list and choose a Region\. For more information, see [Region Name and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of your organization\.

1. In the navigation pane, choose **Users**, and in the list of users, select the name of the user whose device you need to wipe\.

1. Choose the **Mobile devices** tab\.

1. In the list of devices, choose the button next to the device, and then choose **Wipe**\.

1. Check the status in the overview to see whether the wipe is requested\.

1. After the device is wiped, remove it from the devices list\. The steps in the next section explain how\. 
**Important**  
To return a wiped device to a user's list of devices, make sure you first remove it from the wipe list\. Otherwise, the system wipes the device again\.

## Removing user devices from the devices list<a name="remove_mobile_device"></a>

If someone stops using a specific mobile device, or you've remotely wiped the device, you can remove the device from the devices list\. When the user configures the device again, it shows up in the list\.

**To remove a user's mobile devices from the devices list**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of your organization\.

1. In the navigation pane, choose **Users**, and then select the user's name\.

1. Choose the **Mobile devices** tab\.

1. In the list of devices, select the button next to the device and choose **Remove**\.

## Viewing mobile device details<a name="view_device_details"></a>

You can you view the details of a user's mobile device\. 

**Note**  
Some devices don't send all their details to the server\. You may not see all available device details\.

**To view device details**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the Region\. From the navigation bar, select the Region that meets your needs\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of your organization\.

1. In the navigation pane, choose **Users**, and then choose the **Mobile devices** tab\.

1. In the list of devices, select the ID of the device for which you want to view details\. 

   The following table lists the device status codes\.    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/workmail/latest/adminguide/manage-devices.html)