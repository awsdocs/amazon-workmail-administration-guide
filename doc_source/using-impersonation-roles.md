# Using impersonation roles<a name="using-impersonation-roles"></a>

To access mailbox data, use the Amazon WorkMail API action `AssumeImpersonationRole`\. For more details on Amazon WorkMail APIs, see [API Reference](https://docs.aws.amazon.com/workmail/latest/APIReference/Welcome.html)\.

`AssumeImpersonationRole` returns a `Token`\. This `Token` must be passed within 15 minutes to the EWS protocol through the HTTP header `Authorization`\.

The following examples demonstrate how to use impersonation roles with the EWS protocol\. The constants used in the examples specify the following details unique to your organization and account: 
+ `WORKMAIL_ORGANIZATION_ID` – Amazon WorkMail organization ID
+ `IMPERSONATION_ROLE_ID` – Impersonation role ID 
+ `WORKMAIL_EWS_URL` – EWS endpoint available at [Amazon WorkMail endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/workmail.html)
+ `EMAIL_ADDRESS` – Email address of the user mailbox 

**Example Java – [EWS Java API](https://github.com/OfficeDev/ews-java-api)**  

```
import software.amazon.awssdk.services.workmail.WorkMailClient;
import software.amazon.awssdk.services.workmail.model.AssumeImpersonationRoleRequest;
import software.amazon.awssdk.services.workmail.model.AssumeImpersonationRoleResponse;

import microsoft.exchange.webservices.data.core.ExchangeService;
import microsoft.exchange.webservices.data.core.enumeration.misc.ExchangeVersion;
import microsoft.exchange.webservices.data.misc.ImpersonatedUserId;
import microsoft.exchange.webservices.data.core.enumeration.misc.ConnectingIdType;

// ...

AssumeImpersonationRoleResponse response = workMailClient.assumeImpersonationRole(
    AssumeImpersonationRoleRequest.builder()
        .organizationId(WORKMAIL_ORGANIZATION_ID)
        .impersonationRoleId(IMPERSONATION_ROLE_ID)
        .build());

ExchangeService exchangeService = new ExchangeService(ExchangeVersion.Exchange2010_SP2);
exchangeService.setUrl(URI.create(WORKMAIL_EWS_URL));
exchangeService.getHttpHeaders().put("Authorization", "Bearer " + response.token());
exchangeService.setImpersonatedUserId(new ImpersonatedUserId(ConnectingIdType.SmtpAddress, EMAIL_ADDRESS));
```

**Example \.Net – [EWS Managed API](https://github.com/OfficeDev/ews-managed-api)**  

```
using Amazon.WorkMail;
using Amazon.WorkMail.Model;

using Microsoft.Exchange.WebServices.Data;

// ...

AssumeImpersonationRoleRequest request = new AssumeImpersonationRoleRequest();
request.OrganizationId = WORKMAIL_ORGANIZATION_ID;
request.ImpersonationRoleId = IMPERSONATION_ROLE_ID;
AssumeImpersonationRoleResponse response = workMailClient.AssumeImpersonationRole(request);

ExchangeService service = new ExchangeService(ExchangeVersion.Exchange2010_SP2);
service.Url = new Uri(WORKMAIL_EWS_URL);
service.HttpHeaders.Add("Authorization", "Bearer " + response.Token);
service.ImpersonatedUserId = new ImpersonatedUserId(ConnectingIdType.SmtpAddress, EMAIL_ADDRESS);
```

**Example Python – [Exchangelib](https://pypi.org/project/exchangelib/)**  

```
import boto3

from requests.auth import AuthBase
from exchangelib.transport import AUTH_TYPE_MAP
from exchangelib import Configuration, Account, Version, IMPERSONATION
from exchangelib.version import EXCHANGE_2010_SP2


work_mail_client = boto3.client("workmail")

class ImpersonationRoleAuth(AuthBase):
    def __init__(self):
         self.token = work_mail_client.assume_impersonation_role(
             OrganizationId=WORKMAIL_ORGANIZATION_ID,
             ImpersonationRoleId=IMPERSONATION_ROLE_ID
        )["Token"]

     def __call__(self, r):
         r.headers["Authorization"] = "Bearer " + self.token
         return r

AUTH_TYPE_MAP["ImpersonationRoleAuth"] = ImpersonationRoleAuth

ews_config = Configuration(
     service_endpoint=WORKMAIL_EWS_URL,
     version=Version(build=EXCHANGE_2010_SP2),
     auth_type="ImpersonationRoleAuth"
)
ews_account = Account(
     config=ews_config,
     primary_smtp_address=EMAIL_ADDRESS,
     access_type=IMPERSONATION
)
```