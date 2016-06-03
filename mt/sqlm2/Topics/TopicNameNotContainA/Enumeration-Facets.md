---
title: Enumeration Facets
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
---
# Enumeration Facets
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] rejects XML schemas with types that have pattern facets or enumerations that violate those facets.  
  
## Example  
 The following schema would be rejected, because the featured enumeration value includes a mixed\-case value. It would also be rejected because this value violates the pattern value that limits values to only lowercase letters.  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## See Also  
 [Requirements and Limitations for XML Schema Collections on the Server](../../Topics\TopicNameNotContainA/Requirements-and-Limitations-for-XML-Schema-Collections-on-the-Server.md)  
  
  