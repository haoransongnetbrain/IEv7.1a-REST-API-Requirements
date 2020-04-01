
## ***PUT*** /V1/CMDB/Users
Call this API to modify user information.

Note that, all optional fileds are only used to modify the value rather than to clear the value of this filed. so, if this filed is set to null or empty string, no change would be made for this field.

The only way to clear a field is delete a user and add this user back with new value.

## Detail Information

> **Title** : Update User API<br>

> **Version** : 04/01/2020.

> **API Server URL** : http(s)://IP address of NetBrain Web API Server/ServicesAPI/API/V1/CMDB/Users

> **Authentication** : 

|**Type**|**In**|**Name**|
|------|------|------|
|<img width=100/>|<img width=100/>|<img width=500/>|
|Bearer Authentication| Headers | Authentication token |

## Request body(****required***)

|**Name**|**Type**|**Description**|
|------|------|------|
|<img width=100/>|<img width=100/>|<img width=500/>|
|username* | string  | The user name. This parameter is required.  |
|email | string  | The email address of the user. This parameter is required. |
|firstName | string  | The first name of the user. This parameter is required.  |
|lastName | string  | The last name of the user. This parameter is required. |
|password | string  | The login password. The allowed length is 6-128 characters by default. This parameter is required.  |
|authenticationServer **(NetBrain Only?)** | string |The name of the authentication server for create an external account.|
|externalUserIdentity | string |the corresponding external user identity base on the authentication server. This attribute must be inserted when customer want to create an external user account via REST API. 
|phoneNumber | string |The phone number of the user.|
|department | string |The department that the user belongs to.|
|description | string |Any description about the account.|
|allowChangePassword | bool |Specify whether to allow the user to change password independently. This parameter is required.|
|deactivatedTime | datetime |Specify the time when the account is expired.|
|isSystemAdmin | bool |Decide whether to allocate system administrator role to the user. This parameter is required.|
|isSystemManagement | bool |Decide whether to allocate system management role to the user. This parameter is required.|
|isUserManagement | bool |Decide whether to allocate user management role to the user. This parameter is required.|
|TenantsAndDomains | list of tenant object |Specify a list of tenants for the user.<br>Only required if the parameter isSystemAdmin is false.|
|TenantsAndDomains.tenantId| string |the ID of the accessible tenant.|
|TenantsAndDomains.tenantName| string |the tenant that the user can access.|
|TenantsAndDomains.isAdmin| bool |decide whether to allocate the tenant administrator role to the user. If false, you need to specify a domain for the user to access.|
|TenantsAndDomains.canAddDomain| bool | decide whether to allow the user to create domains.|
|TenantsAndDomains.accessibleDomains| list of domain object |required only if the parameter isTenantAdmin is false.|
|TenantsAndDomains.accessibleDomains.domainName| string |the domain name.|
|TenantsAndDomains.accessibleDomains.roles| list of domain user |the role of the domain user.|
|isEmbeddedMapUser| bool |whether current user is an embedded map user.|

**Note：** Only username cannot modified by this API.
> ***Example***


```python
{
            "username": "Suneet45",
            "email": "suneet.tatikonda@netbraintech.com",
            "firstName": "Suneet",
            "lastName": "Tatikonda",
            "authenticationServer" : "XXXX",
            "externalUserIdentity" : "",
            "phoneNumber" : "XXX-XXX-XXXX",
            "department" : "",
            "isEmbeddedMapUser" : true,
            "createdDate" : mm/dd/yyyy hh:mm:ss, # default create by system automatically.
            "deactivatedTime" : mm/dd/yyyy hh:mm:ss,
            "description" : "...",
            "allowChangePassword": true,
            "isSystemAdmin": true,
            "isSystemManagement" : false,
            "isUserManagement" : false,
            "TenantsAndDomains" : [
                {
                    "tenantId" : "...",
                    "tenantName" : "..."
                    "isAdmin" : true,
                    "canAddDomain" : true,
                    "accessibleDomains" : [{
                        "domainName":"domain_cyj",
                        "roles":["domainAdmin"]
                    }]
                },
                .
                .
                .
            ]
            
        }
```


```python

```
