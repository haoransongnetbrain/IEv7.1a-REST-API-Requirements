
# Add User

## ***POST*** /V1/CMDB/Users
Call this API to create a new user account in Netbrain system.

## Detail Information

> **Title** : Add User API<br>

> **Version** : 02/01/2019.

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
|email* | string  | The email address of the user. This parameter is required. |
|firstName* | string  | The first name of the user. This parameter is required.  |
|lastName* | string  | The last name of the user. This parameter is required. |
|password* | string  | The login password. The allowed length is 6-128 characters by default. This parameter is required.  |
|authenticationServer | string |The name of the authentication server for create an external account.|
|externalUserIdentity | string |the corresponding external user identity base one the authentication server. This attribute must be inserted when customer want to create an external user account via REST API. 
|phoneNumber | string |The phone number of the user.|
|department | string |The department that the user belongs to.|
|description | string |Any description about the account.|
|allowChangePassword | bool |Specify whether to allow the user to change password independently. This parameter is required.|
|deactivatedTime | string |Specify the time when the account is expired.|
|isSystemAdmin | bool |Decide whether to allocate system administrator role to the user. This parameter is required.|
|tenants | list of tenant object |Specify a list of tenants for the user.<br>Only required if the parameter isSystemAdmin is false.|
|tenants.tenantName| string |the tenant that the user can access.|
|tenants.isTenantAdmin| bool |decide whether to allocate the tenant administrator role to the user. If false, you need to specify a domain for the user to access.|
|tenants.allowCreateDomain| bool | decide whether to allow the user to create domains.|
|tenants.domains| list of domain object |required only if the parameter isTenantAdmin is false.|
|tenants.domains.domainName| string |the domain name.|
|tenants.domains.domainRoles| list of domain user |the role of the domain user.|
|isEmbeddedMapUser| bool |whether current user is an embedded map user.|
|expiredAfter | date | The expired time of currnt user. |

> ***Example***


```python
{
        "username": "user1",
        "externalUserIdentity":"xxxx",
        "authenticationServer":"sso",
        "email": "user1@sso.com",
        "firstName": "user1",
        "lastName": "user1",
        "password": "user1",
        "phoneNumber" : "",
        "department" : "",
        "description" : "",
        "deactivatedTime" : "",
        "isSystemAdmin":"false",
        "tenants" : [{
            "tenantName":"tenant_71a1",
            "isTenantAdmin":false,
            "allowCreateDomain":"false",
            "domains":[{
                "domainName":"domain_cyj",
                "domainRoles":["domainAdmin"]
            }]
        }]
        "isEmbeddedMapUser" : True/False,
        "expiredAfter" : 03/31/2020
}
```

# Update user


## ***PUT*** /V1/CMDB/Users
Call this API to modify user information.

Note that, all optional fileds are only used to modify the value rather than to clear the value of this filed. so, if this filed is set to null or empty string, no change would be made for this field.

The only way to clear a field is delete a user and add this user back with new value.

## Detail Information

> **Title** : Update User API<br>

> **Version** : 02/01/2019.

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
|email* | string  | The email address of the user. This parameter is required. |
|firstName* | string  | The first name of the user. This parameter is required.  |
|lastName* | string  | The last name of the user. This parameter is required. |
|password* | string  | The login password. The allowed length is 6-128 characters by default. This parameter is required.  |
|authenticationServer | string |The name of the authentication server for create an external account.|
|phoneNumber | string |The phone number of the user.|
|department | string |The department that the user belongs to.|
|description | string |Any description about the account.|
|allowChangePassword | bool |Specify whether to allow the user to change password independently. This parameter is required.|
|deactivatedTime | string |Specify the time when the account is expired.|
|isSystemAdmin | bool |Decide whether to allocate system administrator role to the user. This parameter is required.|
|tenants | list of tenant object |Specify a list of tenants for the user.<br>Only required if the parameter isSystemAdmin is false.|
|tenants.tenantName| string |the tenant that the user can access.|
|tenants.isTenantAdmin| bool |decide whether to allocate the tenant administrator role to the user. If false, you need to specify a domain for the user to access.|
|tenants.allowCreateDomain| bool | decide whether to allow the user to create domains.|
|tenants.domains| list of domain object |required only if the parameter isTenantAdmin is false.|
|tenants.domains.domainName| string |the domain name.|
|tenants.domains.domainRoles| list of domain user |the role of the domain user.|
|isEmbeddedMapUser| bool |whether current user is an embedded map user.|
|expiredAfter | date | The expired time of currnt user. |

> ***Example***


```python
{
        "username": "user1",
        "externalUserIdentity":"xxxx",
        "authenticationServer":"sso",
        "email": "user1@sso.com",
        "firstName": "user1",
        "lastName": "user1",
        "password": "user1",
        "phoneNumber" : "",
        "department" : "",
        "description" : "",
        "deactivatedTime" : "",
        "isSystemAdmin":"false",
        "tenants" : [{
            "tenantName":"tenant_71a1",
            "isTenantAdmin":false,
            "allowCreateDomain":"false",
            "domains":[{
                "domainName":"domain_cyj",
                "domainRoles":["domainAdmin"]
            }]
        }]
        "isEmbeddedMapUser" : True/False,
        "expiredAfter" : 03/31/2020
}
```

# Get User


GET /V1/CMDB/Users{?username}&{?authenticationServer}
-----------------------------------------------------

Calling this API to get user information. If input username, API return just
this one user information. If no specific user name is input, API return all
user information.

Detail Information
------------------

>   **Title** : Get User(s) information API

>   **Version** : 02/06/2019.

>   **API Server URL** : http(s):// IP address of your NetBrain Web API Server
>   /ServicesAPI/API/V1/CMDB/Users

>   **Authentication** :

| **Type**              | **In**     | **Name**             |
|-----------------------|------------|----------------------|
|                       |            |                      |
| Bearer Authentication | Parameters | Authentication token |

Request body(\*\*\*\*required\*\*\*)
------------------------------------

>   No request body.

Query Parameters(\*\*\*\*required\*\*\*)
----------------------------------------

| **Name**             | **Type** | **Description**                                                                                                                                                           |
|----------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      |          |                                                                                                                                                                           |
| username             | string   | The name of Netbrain system user. This field is the key to get the user information. if set "username" = null or "username" == "", API will returns all users information |
| authenticationServer | string   | The corresponding name of the authentication server.                                                                                                                      |

**Note:** the "authenticationServer" is an optional attribute, to prevent
mis-retrieving if there are same user account names exist in different servers.
Check the detail in the following example.

Headers
-------

>   **Data Format Headers**

| **Name**     | **Type** | **Description**            |
|--------------|----------|----------------------------|
|              |          |                            |
| Content-Type | string   | support "application/json" |
| Accept       | string   | support "application/json" |

>   **Authorization Headers**

| **Name** | **Type** | **Description**                           |
|----------|----------|-------------------------------------------|
|          |          |                                           |
| token\*  | string   | Authentication token, get from login API. |

Response
--------

| **Name**                     | **Type**                     | **Description**                                                                                                                                                                                                                                                                                                                       |
|------------------------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                              |                              |                                                                                                                                                                                                                                                                                                                                       |
| UserData                     | list of object               | List of users info.                                                                                                                                                                                                                                                                                                                   |
| UserData.username            | string                       | The user name, this filed is the key to update the user information.                                                                                                                                                                                                                                                                  |
| UserData.email               | string                       | The email address of the user.                                                                                                                                                                                                                                                                                                        |
| UserData.firstName           | string                       | The first name of the user.                                                                                                                                                                                                                                                                                                           |
| UserData.lastName            | string                       | The last name of the user.                                                                                                                                                                                                                                                                                                            |
| UserData.authenticationType  | int                          | The authentication type for the user account.                                                                                                                                                                                                                                                                                         |
|                              |                              | ▪ 1 - Local                                                                                                                                                                                                                                                                                                                           |
|                              |                              | ▪ 2 - External                                                                                                                                                                                                                                                                                                                        |
| UserData.phoneNumber         | string                       | The phone number of the user.                                                                                                                                                                                                                                                                                                         |
| UserData.department          | string                       | The department that the user belongs to.                                                                                                                                                                                                                                                                                              |
| UserData.isEmbeddedMapUser          | bool                       | whether current user is an embedded map user.                                                                                                                                                                                                                                                                                              |
| UserData.authenticationServer          | string                       | The authentication server name of current user                                                                                                                                                                                                                                                                                               |
| UserData.createdDate          | Date                       | The time of current user created.                                                                                                                                                                                                                                                                                              |
| UserData.description         | string                       | Any description about the user.                                                                                                                                                                                                                                                                                                       |
| UserData.allowChangePassword | bool                         | Decide whether to allow the user to change his/her password independently.                                                                                                                                                                                                                                                            |
| UserData.deactivatedTime     | string                       | Specify the time when the user account is expired.                                                                                                                                                                                                                                                                                    |
| UserData.isSystemAdmin       | string                       | Decide whether to allocate the system administrator role to the user.                                                                                                                                                                                                                                                                 |
| UserData.TenantAndRole       | list of TenantAndRole object | Specify Tenant And Role for the user.                                                                                                                                                                                                                                                                                                 |
|                              |                              | ▪ tenantId (string) - the tenant that the user can access.                                                                                                                                                                                                                                                                            |
|                              |                              | ▪ isAdmin(bool) - decide whether to allocate the tenant administrator role to the user. If it is false, you need to specify a domain for the user to access.                                                                                                                                                                          |
|                              |                              | ▪ canAddDomain(bool) - decide whether to allow the user to create domains.                                                                                                                                                                                                                                                            |
|                              |                              | ▪ accessibleDomain(list of string) - all domains can be access by this user.                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                   
| users                        | list of object               | The list contains the dupilcate account information in different server.                                                                                                                                                                                                                                                              |
| users.userName               | string                       | The name of the user account.                                                                                                                                                                                                                                                                                                         |
| users.authenticationServer   | string                       | The name of authentication server.                                                                                                                                                                                                                                                                                                    |
| statusCode                   | integer                      | Code issued by NetBrain server indicating the execution result.                                                                                                                                                                                                                                                                       |
| statusDescription            | bool                         | The explanation of the status code.                                                                                                                                                                                                                                                                                                   |

>   **Example**


```python
{
    "UserData": [
        {
            "username": "Suneet45",
            "email": "suneet.tatikonda@netbraintech.com",
            "firstName": "Suneet",
            "lastName": "Tatikonda",
            "authenticationType" : 0/1,
            "authenticationServer" : "XXXX",
            "phoneNumber" : "XXX-XXX-XXXX",
            "department" : "",
            "isEmbeddedMapUser" : True/False,
            "createdDate" : 03/31/2020,
            "deactivatedTime" : 03/31/2021,
            "description" : "...",
            "allowChangePassword": true,
            "isSystemAdmin": true,
            "TenantAndRole" : [
                {
                    "tenantId" : "..",
                    "isAdmin" : True/False,
                    "canAddDomain" : True/False,
                    "accessibleDomain" : []
                },
                .
                .
                .
            ]
            "users" : [
                {
                    "userName" : "XXX",
                    "authenticationServer" : "XXX"
                },
                .
                .
                .
            ]
        }
    ]
}
```
