# Enabling AutoDiscover to configure endpoints<a name="autodiscover"></a>

AutoDiscover enables you to configure Microsoft Outlook and mobile clients by using only your email address and password\. The service maintains a connection to Amazon WorkMail and updates local settings whenever you change endpoints or settings\. In addition, AutoDiscover enables your client to use additional Amazon WorkMail features, such as the Offline Address Book, Out\-of\-Office Assistant, and the ability to view free/busy time in Calendar\. 

The client performs the following AutoDiscover phases to detect the server endpoint URLs:
+ **Phase 1** – The client performs a Secure Copy Protocol \(SCP\) lookup against the local Active Directory\. If your client isn’t domain\-joined, AutoDiscover skips this step\.
+ **Phase 2** – The client sends a request to the following URLs and validates the results\. These endpoints are only available using HTTPS\.
  + https://*company\.tld*/autodiscover/autodiscover\.xml 
  + https://autodiscover\.*company\.tld*/autodiscover/autodiscover\.xml
+ **Phase 3** – The client performs a DNS lookup to autodiscover\.company\.tld and sends an unauthenticated GET request to the derived endpoint from the user’s email address\. If the server returns a 302 redirect, the client resends the AutoDiscover request against the returned HTTPS endpoint\. 

If all of these phases fail, the client can’t be configured automatically\. For information about manually configuring mobile devices, see [Manually connect your device](https://docs.aws.amazon.com/workmail/latest/userguide/manually_connect_device.html)\.

You are prompted to add the AutoDiscover DNS record to your provider when you add your domain to Amazon WorkMail\. This enables the client to perform phase 3 of the AutoDiscover process\. However, these steps don't work for all mobile devices, such as the stock Android email app\. As a result, you may need to set up AutoDiscover phase 2 manually\.

You can use the following methods to set up AutoDiscover phase 2 for your domain:

## \(Recommended\) Use Route 53 and Amazon CloudFront<a name="use-r53"></a>

**Note**  
The following steps explain how to create a proxy for https://autodiscover\.*company\.tld*/autodiscover/autodiscover\.xml\. To create a proxy for https://*company\.tld*/autodiscover/autodiscover\.xml, remove the `autodiscover.` prefix from the domains in the following steps\.  
Using CloudFront and Route 53 may incure charges\. For more information about applicable pricing, see [Amazon CloudFront pricing](https://aws.amazon.com/cloudfront/pricing/) and [Amazon Route 53 pricing](https://aws.amazon.com/route53/pricing/)\.

**To enable AutoDiscover phase 2 with Route 53 and CloudFront**

1. Get an SSL certificate for autodiscover\.*company\.tld* and upload it to AWS Identity and Access Management \(IAM\) or AWS Certificate Manager\. For more information, see [Working with server certificates](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_server-certs.html) in the *IAM User Guide*, or [Getting started](https://docs.aws.amazon.com/acm/latest/userguide/gs.html) in the *AWS Certificate Manager User Guide*\.

1. Create a new CloudFront distribution:

   1. Open the CloudFront console at [https://console.aws.amazon.com/cloudfront/v3/home](https://console.aws.amazon.com/cloudfront/v3/home)\.

   1. In the navigation pane, choose **Distributions**\.

   1. Choose **Create Distribution**\.

   1. Under **Web**, choose **Get Started**\. 

   1. In **Origin Settings**, enter the following values:
      + **Origin Domain Name** – The appropriate domain name for your Region: 
        + US East \(N\. Virginia\) — **autodiscover\-service\.mail\.us\-east\-1\.awsapps\.com**
        + US West \(Oregon\) — **autodiscover\-service\.mail\.us\-west\-2\.awsapps\.com**
        + Europe \(Ireland\) — **autodiscover\-service\.mail\.eu\-west\-1\.awsapps\.com**

        
      + **Origin Protocol Policy** – The desired policy: **Match Viewer**
**Note**  
Leave **Origin path** blank\. Don't change the auto\-populated value for **Origin ID**\.

   1. In **Default Cache Behavior Settings**, select the following values for the listed settings:
      + **Viewer Protocol Policy**: HTTPS Only
      + **Allowed HTTP Methods**: GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE
      + **Cache Based on Selected Request Headers**: All
      + **Forward Cookies**: All
      + **Query String Forwarding and Caching**: None \(Improves Caching\) 
      + **Smooth Streaming**: No 
      + **Restrict Viewer Access**: No 

   1. Select the following values for **Distribution Settings**:
      + **Price Class**: Use only US, Canada, and Europe
      + For **Alternate Domain Names \(CNAMEs\)**, enter **autodiscover\.*company\.tld*** or ***company\.tld***, where *company\.tld* is your domain name\.
      + **SSL Certificate**: Custom SSL Certificate \(stored in IAM\)
      + **Custom SSL Client Support**: Choose **All Clients** or **Only Clients that Support Server Name Indication \(SNI\)**\. Older versions of Android might not work with the latter option\.
**Note**  
If you choose **All Clients**, leave **Default Root Object** blank\.
      + **Logging**: Choose **On** or **Off**\. **On** enables logging\. 
      + For **Comment**, enter **AutoDiscover type2 for autodiscover\.*company\.tld***
      + **Distribution State**: choose **Enabled**\.

   1. Choose **Create Distribution**\.

1. In the Route 53 console, create a record that routes internet traffic for your domain name to your CloudFront distribution\.
**Note**  
These steps assume that the DNS record for example\.com is hosted on Route 53\. If you don't use Route 53, follow the procedures in your DNS provider's management console\. 

   1. In the console's navigation pane, choose **Hosted Zones**\. and then choose a domain\. 

   1. In the list of domains, choose the domain name that you want to use\.

   1. In **Records**, choose **Create record**\.

   1. Under **Quick create record**, set the following parameters:
      + Under **Record Name**, enter a name for the record\. 
      + Under **Routing policy**, select **Simple routing**\.
      + Choose the **Alias** slider to turn it on\. The slider turns blue when in the on state\.
      + In the **Record type** list, choose **A \- Routes traffic to an IPv4 address and some AWS resources**\.
      + In the **Route traffic to** list, choose **Alias to CloudFront distribution**\.
      + A search box will appear beneath the **Route traffic to** list\. Enter your CloudFront distribution's name into the text box\. You can also select your distribution from the list that appears when you select the search box\.

   1. Choose **Create record**\.

## Use an Apache web server<a name="use-apache"></a>

The following steps explain how to use an Apache web server to create a proxy for https://autodiscover\.*company\.tld*/autodiscover/autodiscover\.xml\. To create a proxy for https://*company\.tld*/autodiscover/autodiscover\.xml, remove the "autodiscover\." prefix from the domains in the following steps\.

**To enable AutoDiscover phase 2 with an Apache web server**

1. Run the following directives on an SSL\-enabled Apache server: 

   ```
   SSLProxyEngine on ProxyPass /autodiscover/autodiscover.xml https://autodiscover-service.mail.REGION.awsapps.com/autodiscover/autodiscover.xml
   ```

1. As needed, enable the following Apache modules\. If you don't know how, refer to the Apache help:
   + `proxy`
   + `proxy_http`
   + `socache_shmcb`
   + `ssl`

See the following section for information about testing and troubleshooting AutoDiscover\.

## AutoDiscover phase 2 troubleshooting<a name="troubleshooting"></a>

Once you've configured your DNS provider for AutoDiscover, you can test your AutoDiscover endpoint configuration\. If you've configure your endpoint correctly, it responds with an unauthorized request message\.

**To make a basic unauthorized request**

1. From a terminal, create an unauthenticated POST request to the AutoDiscover endpoint\.

   ```
   $ curl -X POST -v https://autodiscover.''company.tld''/autodiscover/autodiscover.xml
   ```

   If your endpoint is configured correctly, it should return a `401 unauthorized` message, as shown in the following example:

   ```
   $ curl -X POST -v https://autodiscover.''company.tld''/autodiscover/autodiscover.xml
   ...
   HTTP/1.1 401 Unauthorized
   ```

1. Next, test a real AutoDiscover request\. Create a `request.xml` file with the following XML content:

   ```
   <?xml version="1.0" encoding="utf-8"?> 
   
   <Autodiscover xmlns="http://schemas.microsoft.com/exchange/autodiscover/mobilesync/requestschema/2006">
       <Request>
           <EMailAddress>testuser@company.tld</EMailAddress>
           <AcceptableResponseSchema>
               http://schemas.microsoft.com/exchange/autodiscover/mobilesync/responseschema/2006
           </AcceptableResponseSchema>      
       </Request>
   </Autodiscover>
   ```

1. Use the `request.xml` file you created and make an authenticated AutoDiscover request to the endpoint\. Remember to replace *testuser@company\.tld* with a valid email address:

   ```
   $ curl -d @request.xml -u testuser@company.tld -v https://autodiscover.company.tld/autodiscover/autodiscover.xml
   ```

   The response will look similar to the following example if the endpoint is configured correctly:

   ```
   $ curl -d @request.xml -u testuser@company.tld -v https://autodiscover.company.tld/autodiscover/autodiscover.xml
   
   Enter host password for user 'testuser@company.tld':
   <?xml version="1.0" encoding="UTF-8"?>
   <Autodiscover xmlns="http://schemas.microsoft.com/exchange/autodiscover/responseschema/2006" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <Response xmlns="http://schemas.microsoft.com/exchange/autodiscover/mobilesync/responseschema/2006">
       <Culture>en:us</Culture>
       <User>
           <DisplayName>User1</DisplayName>
           <EMailAddress>testuser@company.tld</EMailAddress>
       </User>
       <Action>
           <Settings>
               <Server>
                   <Type>MobileSync</Type>
                   <Url>https://mobile.mail.us-east-1.awsapps.com/Microsoft-Server-ActiveSync</Url>
                   <Name>https://mobile.mail.us-east-1.awsapps.com/Microsoft-Server-ActiveSync</Name>
               </Server>
           </Settings>
       </Action>
   </Response>
   ```