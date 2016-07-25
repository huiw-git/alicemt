---
title: "isWrapperFor Method (SQLServerXADataSource)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d612461d-4c3f-46db-b968-ff4c80b2aa7c
caps.latest.revision: 9
manager: jhubbard
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
# isWrapperFor Method (SQLServerXADataSource)
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
 The [isWrapperFor](../content/isWrapperFor-Method--SQLServerXADataSource-.md) method and the [unwrap](../content/unwrap-Method--SQLServerXADataSource-.md) method are defined by the java.sql.Wrapper interface, which is introduced in the JDBC 4.0 Spec.  
  
 If this method returns true, calling [unwrap](../content/unwrap-Method--SQLServerXADataSource-.md) with the same argument will succeed.  
  
 For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [unwrap Method &#40;SQLServerXADataSource&#41;](../content/unwrap-Method--SQLServerXADataSource-.md)   
 [SQLServerXADataSource Methods](../content/SQLServerXADataSource-Methods.md)   
 [SQLServerXADataSource Members](../content/SQLServerXADataSource-Members.md)   
 [SQLServerXADataSource Class](../content/SQLServerXADataSource-Class.md)  
  
  