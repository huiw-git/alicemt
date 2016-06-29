---
title: isWrapperFor Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 53f3291f-d43a-476b-a656-d86168dacf6c
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
# isWrapperFor Method (SQLServerStatement)
  Indicates whether this statement object is a wrapper for the specified interface.  
  
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
 The [isWrapperFor](../content/isWrapperFor-Method--SQLServerStatement-.md) method and the [unwrap](../content/unwrap-Method--SQLServerStatement-.md) method are defined by the java.sql.Wrapper interface, which is introduced in JDBC 4.0.  
  
 If this method returns true, calling [unwrap](../content/unwrap-Method--SQLServerStatement-.md) with the same argument will succeed.  
  
 For an example code, see [Updating Large Data Sample](../content/Updating-Large-Data-Sample.md).  
  
 For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [unwrap Method &#40;SQLServerStatement&#41;](../content/unwrap-Method--SQLServerStatement-.md)   
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  