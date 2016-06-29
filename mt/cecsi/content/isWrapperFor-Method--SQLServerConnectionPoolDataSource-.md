---
title: isWrapperFor Method (SQLServerConnectionPoolDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09ed10eb-6e46-437b-a7c0-3c55574aad38
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# isWrapperFor Method (SQLServerConnectionPoolDataSource)
  Indicates whether this object is a wrapper for the specified interface.  
  
## Syntax  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### Parameters  
 *iface*  
  
 A **class** defining an interface.  
  
## Return Value  
 **true** if this object implements the interface or wraps an object that implements the interface. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 The [isWrapperFor](../content/isWrapperFor-Method--SQLServerXADataSource-.md) method and the [unwrap](../content/unwrap-Method--SQLServerConnectionPoolDataSource-.md) method are defined by the java.sql.Wrapper interface, which is introduced in the JDBC 4.0 Spec.  
  
 If this method returns true, calling [unwrap](../content/unwrap-Method--SQLServerConnectionPoolDataSource-.md) with the same argument will succeed.  
  
 For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [unwrap Method &#40;SQLServerConnectionPoolDataSource&#41;](../content/unwrap-Method--SQLServerConnectionPoolDataSource-.md)   
 [SQLServerConnectionPoolDataSource Methods](../content/SQLServerConnectionPoolDataSource-Methods.md)   
 [SQLServerConnectionPoolDataSource Members](../content/SQLServerConnectionPoolDataSource-Members.md)   
 [SQLServerConnectionPoolDataSource Class](../content/SQLServerConnectionPoolDataSource-Class.md)  
  
  