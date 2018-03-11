# Remotely Wipe Mobile Devices<a name="remote_wipe_device"></a>

You can only remotely wipe user devices when they are connected to Amazon WorkMail\. If a device is disconnected from the network, this procedure doesn't work\.

**Warning**  
For most mobile devices, a remote wipe resets the device to factory defaults\. All data, including personal files, can be removed when you perform this procedure\.

**To remotely wipe a user's mobile device**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

1. If necessary, change the region\. From the navigation bar, select the region that meets your needs\. For more information, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. On the **Organizations** screen, in the list of organizations, select your organization's alias\.

1. In the navigation pane, choose **Users**, select the user with the device to view, and choose **Mobile**\.

1. In the list of devices, select the device to wipe and choose **Wipe device**\.

1. Check the status in overview to see whether the wipe is requested\.

1. After the device is wiped, you can remove the device from the list\.
**Important**  
To re\-add a device, make sure the device is removed from the list; otherwise, the device will be wiped again\.