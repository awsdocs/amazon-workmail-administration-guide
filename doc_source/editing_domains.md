# Editing domain identity policies<a name="editing_domains"></a>

Domain identity policies specify permissions for email actions, such as redirecting email messages\. For example, you can redirect emails to any email address in your Amazon WorkMail organization\.

**Note**  
As of April 1, 2022, Amazon WorkMail began using service principals for authorization instead of AWS account principals\. If you added a domain prior to April 1, 2022 you may have an older policy that uses an AWS account principal for authorization\. If so, we recommend updating to the latest policy\. The steps in this section explain how\. Your organization continues to send emails normally during the update\.

You only follow these steps if you don't use a custom Amazon SES policy\. If you use a custom Amazon SES policy, you must update it yourself\. For more information, see [Custom Amazon SES service\-principal policy](#custom-ses-policy), later in this topic\. 

**Important**  
Don't remove your existing domains\. If you do, you'll disrupt mail service\. All you need to do is re\-enter your existing domains\.

**To update a domain identity policy**

1. Open the Amazon WorkMail console at [https://console\.aws\.amazon\.com/workmail/](https://console.aws.amazon.com/workmail/)\.

   If necessary, change the AWS Region\. To do so, open the **Select a region** list, located to the right of the search box, then choose the desired region\. For more information about regions, see [Regions and endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *Amazon Web Services General Reference*\.

1. In navigation pane, choose **Organizations**, and then choose name of your organization\.

1. In the navigation pane, choose **Domains**\.

1. Highlight and copy the name of the domain that you want to re\-enter, and then choose **Add Domain**\.

   The **Add domain** dialog box appears\.

1. Paste the copied name into the **Domain name** box, and then choose **Add domain**\.

1. Repeat steps 3\-5 for the remaining domains in your organization\.

## Custom Amazon SES service\-principal policy<a name="custom-ses-policy"></a>

If you use a custom Amazon SES policy, adapt this example for use in your domain\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AuthorizeWorkMail",
      "Effect": "Allow",
      "Principal": {
        "Service": "workmail.REGION.amazonaws.com"
      },
      "Action": [
        "ses:*"
      ],
      "Resource": "arn:aws:ses:REGION:AWS_ACCOUNT_ID:identity/WORKMAIL-DOMAIN-NAME",
      "Condition": {
        "ArnEquals": {
          "aws:SourceArn": "arn:aws:workmail:REGION:AWS_ACCOUNT_ID:organization/WORKMAIL_ORGANIZATION_ID"
        }
      }
    }
  ]
}
```