---
title: KeyValuePairOfstringstring Data Object - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: Matt-UX
ms.author: matrob
description: The list of key and value strings to avoid otherwise breaking changes in the current Customer Management API version.
---
# KeyValuePairOfstringstring Data Object - Customer Management
The list of key and value strings to avoid otherwise breaking changes in the current Customer Management API version.

## Syntax
```xml
<xs:complexType name="KeyValuePairOfstringstring" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:annotation>
    <xs:appinfo>
      <GenericType Name="KeyValuePairOf{0}{1}{#}" Namespace="http://schemas.datacontract.org/2004/07/System.Collections.Generic" xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
        <GenericParameter Name="string" Namespace="http://www.w3.org/2001/XMLSchema" />
        <GenericParameter Name="string" Namespace="http://www.w3.org/2001/XMLSchema" />
      </GenericType>
      <IsValueType xmlns="http://schemas.microsoft.com/2003/10/Serialization/">true</IsValueType>
    </xs:appinfo>
  </xs:annotation>
  <xs:sequence>
    <xs:element name="key" nillable="true" type="xs:string" />
    <xs:element name="value" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="elements"></a>Elements

The [KeyValuePairOfstringstring](keyvaluepairofstringstring.md) object has the following elements: [key](#key), [value](#value).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="key"></a>key|The name of the setting.|**string**|
|<a name="value"></a>value|The value of the setting.|**string**|

## Requirements
Service: [CustomerManagementService.svc v13](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v13/CustomerManagementService.svc)  
Namespace: http\://schemas.datacontract.org/2004/07/System.Collections.Generic  

## Used By
[AdvertiserAccount](advertiseraccount.md)  
[ClientLink](clientlink.md)  
[Customer](customer.md)  
[User](user.md)  
