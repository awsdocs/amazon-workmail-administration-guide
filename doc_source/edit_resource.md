# Editing resource details<a name="edit_resource"></a>

You can edit a resource's general details, including name, description, type, and email address, as well as booking options and delegates\. 

**To edit general resource details**



1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the name of your organization\.

1. In the navigation pane, choose **Resources**, and then select the resource to edit\.

1. On the **General** tab, update the **Resource name**, **Description**, **Resource Type**, or **Email address** details as needed\.

1. Choose **Save**\.

You can configure a resource to accept or decline booking requests automatically\.

**To enable or disable automatic processing of booking requests**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, and then choose the name of your organization\.

1. In the navigation pane, choose **Resources**, and then select the resource to edit\. A page appears and displays **Resource details** and two tabs, **Booking options** and **Delegates**\.

   Do any of the following:

**To change a resource's details**

   1. In the **Resource details** section, choose **Edit**\.

   1. As needed, change the resource's name, description, or type\.

**To add an email alias to a resource**

   1. In the **Resource details** section, choose **Edit**\.

   1. Under **Email address**, choose **Add alias**\.

   1. In the **Email aliases** box, enter an alias\.

   1. Repeat steps 2 and 3 as desired to enter more aliases\.

   1. Choose **Save changes**\.

**To change a resource's booking options**

   1. In the **Booking options** section, choose **Edit**\.

   1. As desired, select or clear the checkbox next to an option to enable or disable the option\.
**Note**  
When you disable any of the automatic booking options, you must create a delegate to handle the booking requests\. The next steps explain how to create delegate\. 

   1. Choose **Save**\.

You can add a delegate to control booking requests for a resource that doesn't have automatic booking options configured\. Resource delegates automatically receive copies of all booking requests and have full access to the resource calendar\. In addition, they must accept all booking requests for a resource\.

**To add a resource delegate**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. In the bar at the top of the console window, open the **Select a Region** list and choose a Region\. For more information, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In the navigation pane, choose **Organizations**, then choose the name of the organization that you want to create delegates for\.

1. In the navigation pane, choose **Resources**, and then select the name of the resource to which you want to add a delegate\.

1. In the **Booking options** tab, choose **Edit**, clear the **Automatically accept all resource requests** checkbox, and then choose **Save**\.

1. Choose the **Delegates** tab, and then choose **Add delegate**\. 

   The **Add delegate** dialog box appears\.

1. Open the **Search delegates** list and choose a delegate, then choose **Save**\.