---
title: SendUserInvitation Service Operation - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Sends an email invitation for someone to manage your Bing Ads accounts.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
> [!IMPORTANT]
> The Bing Ads API Version 13 preview documentation is subject to change. To view version 12 content, use the version selector near the table of contents at the top and left side of the page.

# SendUserInvitation Service Operation - Customer Management
Sends an email invitation for someone to manage your Bing Ads accounts. The recipient can accept the invitation and sign up with credentials that differ from the invitation email address.  

It is possible to have multiple pending invitations sent to the same email address, which have not yet expired. It is also possible for those invitations to have specified different user roles, for example if you sent an invitation with an incorrect user role and then sent a second invitation with the correct user role. The recipient can accept any of the invitations. The Bing Ads API does not support any operations to delete pending user invitations. After you invite a user, the only way to cancel the invitation is through the Bing Ads web application. You can find both pending and accepted invitations in the Users section of Accounts & Billing.

Since a recipient can accept the invitation and sign up with credentials that differ from the invitation email address, you cannot determine with certainty the mapping from a [UserInvitation](userinvitation.md) to a [User](user.md) object. You can search by the invitation ID (returned by *SendUserInvitations*), only to the extent of finding out whether or not the invitation has been accepted or has expired. The [SearchUserInvitations](searchuserinvitations.md) operation returns all pending invitations, whether or not they have expired. Accepted invitations are not included in the [SearchUserInvitations](searchuserinvitations.md) response.  

After the invitation has been accepted, you can call [GetUsersInfo](getusersinfo.md) and [GetUser](getuser.md) to access the Bing Ads user details. Once again though, since a recipient can accept the invitation and sign up with credentials that differ from the invitation email address, you cannot determine with certainty the mapping from a [UserInvitation](userinvitation.md) to a [User](user.md) or [UserInfo](userinfo.md) object. With the user ID returned by [GetUsersInfo](getusersinfo.md) or [GetUser](getuser.md), you can call [DeleteUser](deleteuser.md) to remove the user.

> [!IMPORTANT]
> With Bing Ads multi-user credentials you can accept an invitation to manage a separate customer with your existing Bing Ads credentials. By adding multi-user access to your existing user name, you effectively extend your reach by being able to access other people's accounts. The nice part: You don't need to remember another set of user names and passwords, and you don't need to log in and out of Bing Ads to view different accounts owned by other people. If you accept the invitation with existing Bing Ads credentials, you will have multi-user credentials. It is also possible to contact support directly and have multiple user names consolidated to a single user name i.e., one login will have multi-user permissions. For more details, see [Multi-User Credentials](../guides/customer-accounts.md#multi-user). 

For more information about user authentication, see [Authentication with OAuth](../guides/authentication-oauth.md).

## <a name="request"></a>Request Elements
The *SendUserInvitationRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="userinvitation"></a>UserInvitation|The user invitation to send.|[UserInvitation](userinvitation.md)|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *SendUserInvitationResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="userinvitationid"></a>UserInvitationId|A system-generated identifier for the user invitation that was sent.|**long**|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-header) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <Action mustUnderstand="1">SendUserInvitation</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <SendUserInvitationRequest xmlns="https://bingads.microsoft.com/Customer/v13">
      <UserInvitation xmlns:e179="https://bingads.microsoft.com/Customer/v13/Entities" i:nil="false">
        <e179:Id>ValueHere</e179:Id>
        <e179:FirstName i:nil="false">ValueHere</e179:FirstName>
        <e179:LastName i:nil="false">ValueHere</e179:LastName>
        <e179:Email i:nil="false">ValueHere</e179:Email>
        <e179:CustomerId>ValueHere</e179:CustomerId>
        <e179:RoleId>ValueHere</e179:RoleId>
        <e179:AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
          <a1:long>ValueHere</a1:long>
        </e179:AccountIds>
        <e179:ExpirationDate>ValueHere</e179:ExpirationDate>
        <e179:Lcid>ValueHere</e179:Lcid>
      </UserInvitation>
    </SendUserInvitationRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
This template was generated by a tool to show the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <SendUserInvitationResponse xmlns="https://bingads.microsoft.com/Customer/v13">
      <UserInvitationId>ValueHere</UserInvitationId>
    </SendUserInvitationResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<SendUserInvitationResponse> SendUserInvitationAsync(
	UserInvitation userInvitation)
{
	var request = new SendUserInvitationRequest
	{
		UserInvitation = userInvitation
	};

	return (await CustomerManagementService.CallAsync((s, r) => s.SendUserInvitationAsync(r), request));
}
```
```java
static SendUserInvitationResponse sendUserInvitation(
	UserInvitation userInvitation) throws RemoteException, Exception
{
	SendUserInvitationRequest request = new SendUserInvitationRequest();

	request.setUserInvitation(userInvitation);

	return CustomerManagementService.getService().sendUserInvitation(request);
}
```
```php
static function SendUserInvitation(
	$userInvitation)
{

	$GLOBALS['Proxy'] = $GLOBALS['CustomerManagementProxy'];

	$request = new SendUserInvitationRequest();

	$request->UserInvitation = $userInvitation;

	return $GLOBALS['CustomerManagementProxy']->GetService()->SendUserInvitation($request);
}
```
```python
response=customermanagement_service.SendUserInvitation(
	UserInvitation=UserInvitation)
```

## Requirements
Service: [CustomerManagementService.svc v13](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v13/CustomerManagementService.svc)  
Namespace: https\://bingads.microsoft.com/Customer/v13  
