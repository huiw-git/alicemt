---
title: The xs:QName Type
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
---
# The xs:QName Type
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support types derived from **xs:QName** by the use of an XML Schema restriction element. Also, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] currently does not support union types with **QName** as a member type.  
  
## Example  
 The following `CREATE XML SCHEMA COLLECTION` statements cannot load the XML schema, because they specify the `xs:QName` type as a member type of the union:  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 Both statements fail with an error.  
  
## See Also  
 [Requirements and Limitations for XML Schema Collections on the Server](../../Topics\TopicNameNotContainA/Requirements-and-Limitations-for-XML-Schema-Collections-on-the-Server.md)  
  
  