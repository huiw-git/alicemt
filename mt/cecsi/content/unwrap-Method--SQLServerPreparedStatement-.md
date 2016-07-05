---
title: unwrap Method (SQLServerPreparedStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e3ec950-3ac1-4c28-9e97-ddce3bd46578
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
# unwrap Method (SQLServerPreparedStatement)
  Returns an object that implements the specified interface to allow access to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific methods.  
  
## Syntax  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### Parameters  
 *iface*  
  
 A class of type **T** defining an interface.  
  
## Return Value  
 An object that implements the specified interface.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 The [unwrap](../content/unwrap-Method--SQLServerPreparedStatement-.md) method is defined by the java.sql.Wrapper interface, which is introduced in the JDBC 4.0 Spec.  
  
 Applications might need to access extensions to the JDBC API that are specific to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]. The unwrap method supports unwrapping to public classes that this object extends, if the classes expose vendor extensions.  
  
 When this method is called, the object unwraps to the following classes: [SQLServerStatement](../content/SQLServerStatement-Class.md) and [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md).  
  
 For example code, see [unwrap Method &#40;SQLServerCallableStatement&#41;](../content/unwrap-Method--SQLServerCallableStatement-.md).  
  
 For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [isWrapperFor Method &#40;SQLServerPreparedStatement&#41;](../content/isWrapperFor-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  