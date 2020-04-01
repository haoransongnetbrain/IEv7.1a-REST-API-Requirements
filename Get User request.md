
***GET*** ServicesAPI/API/V1/CMDB/Users
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

Request body(****required***)
------------------------------------

>   No request body.

Query Parameters(****required***)
----------------------------------------

| **Name**             | **Type** | **Description**                                                                                                                                                           |
|----------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                      |          |                                                                                                                                                                           |
| username             | string   | The name of Netbrain system user. This field is the key to get the user information. if set "username" = null or "username" == "", API will returns all users information |
| authenticationServer | string   | The corresponding name of the authentication server.                                                                                                                      |
|version* | int | 1 |

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
| UserData.lastName            | string                       | The last name of the user.                                                                                                                                                                                                                                                                                                   |
| UserData.phoneNumber         | string                       | The phone number of the user.                                                                                                                                                                                                                                                                                                         |
| UserData.department          | string                       | The department that the user belongs to.                                                                                                                                                                                                                                                                                              |
| UserData.isEmbeddedMapUser          | bool                       | whether current user is an embedded map user.                                                                                                                                                                                                                                                                                              |
| UserData.authenticationServer          | string                       | The authentication server name of current user |
|       |         |**Note:** need to confirm that whether duplicate name is allowed. |
| UserData.authenticationType  | int                          | The authentication type for the user account.                                                                                                                                                                                                                                                                                         |
|                              |                              | ▪ 1 - Local                                                                                                                                                                                                                                                                                                                           |
|                              |                              | ▪ 2 - External                                                                                                                                                                                                                                                                                                                        |
| UserData.createdDate          | datetime                       | The time of current user created. |
| UserData.status | string | The status of current user, enable or not.|
| UserData.description         | string                       | Any description about the user.                                                                                                                                                                                                                                                                                                       |
| UserData.allowChangePassword | bool                         | Decide whether to allow the user to change his/her password independently.                                                                                                                                                                                                                                                            |
| UserData.resetPasswordDate | datetime                         | the last date time when customer reset password. (format: mm/dd/yyyy hh:mm:ss)                                                                                                                                                                                                                                                        |
| UserData.deactivatedTime     | string                       | Specify the time when the user account is expired.                                                                                                                                                                                                                                                                                    |
| UserData.isSystemAdmin       | bool                       | Decide whether to allocate the system administrator role to the user.                                                                                                                                                                                                                                                                 |
| UserData.isSystemManagement       | bool                       | Decide whether to allocate the system administrator role to the user.                                                                                                                                                                                                                                                                 |
| UserData.isUserManagement       | bool                       | Decide whether to allocate the system administrator role to the user.                                                                                                                                                                                                                                                                 |
| UserData.TenantAndDomain       | list of TenantAndDomain object | Specify Tenant And Role for the user.                                                                                                                                                                                                                                                                                                 |
|                              |                              | ▪ tenantId (string) - the tenant that the user can access.                                                                                                                                                                                                                                                                            |
|                              |                              | ▪ tenantName (string) - the tenant name that the user can access.                                                                                                                                                                                                                                                                            |
|                              |                              | ▪ isAdmin(bool) - decide whether to allocate the tenant administrator role to the user. If it is false, you need to specify a domain for the user to access.                                                                                                                                                                          |
|                              |                              | ▪ canAddDomain(bool) - decide whether to allow the user to create domains.                                                                                                                                                                                                                                                            |
|                              |                              | ▪ accessibleDomain(list of domain object) - all domains can be access by this user.                                                                                                                                                                                                                                                            |    
|                              |                              | ▪ accessibleDomain.domainName(string) - domainname of one accessible domain.                                                                                                                                                                     |   
|                              |                              | ▪ accessibleDomain.domainRoles(list of string) - all assigned roles of user in current domain.                                                                                                                                                                                                                                                            |   
|**Note:** with username specified in query parameter, if duplicate records found, return response format as below:|  |   | 
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
            "authenticationServer" : "XXXX",
            "externalUserIdentity" : "",
            "phoneNumber" : "XXX-XXX-XXXX",
            "department" : "",
            "isEmbeddedMapUser" : true,
            "createdDate" : mm/dd/yyyy hh:mm:ss,
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
                    "accessibleDomain" : [{
                        "domainName":"domain_cyj",
                        "roles":["domainAdmin"]
                    }]
                },
                .
                .
                .
            ]
            
        }
    ]
}


#with username specified in query parameter, if duplicate records found, return response format as below:
"users" : [
                {
                    "userName" : "XXX",
                    "authenticationServer" : "XXX"
                },
                .
                .
                .
            ]
```
