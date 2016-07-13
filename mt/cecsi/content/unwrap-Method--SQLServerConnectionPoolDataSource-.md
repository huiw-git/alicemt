---
title: unwrap Method (SQLServerConnectionPoolDataSource)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5c9b734-2096-4ae4-a284-6b4d1b4a00d4
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
# unwrap Method (SQLServerConnectionPoolDataSource)
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
 The [unwrap](../content/unwrap-Method--SQLServerConnectionPoolDataSource-.md) method is defined by the java.sql.Wrapper interface, which is introduced in the JDBC 4.0 Spec.  
  
 Applications might need to access extensions to the JDBC API that are specific to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]. The unwrap method supports unwrapping to public classes that this object extends, if the classes expose vendor extensions.  
  
 The [SQLServerConnectionPoolDataSource](../content/SQLServerConnectionPoolDataSource-Class.md) class extends the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) class. When this method is called, the object unwraps to the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) class and the [SQLServerConnectionPoolDataSource](../content/SQLServerConnectionPoolDataSource-Class.md) class.  
  
 For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [SQLServerConnectionPoolDataSource Methods](../content/SQLServerConnectionPoolDataSource-Methods.md)   
 [SQLServerConnectionPoolDataSource Members](../content/SQLServerConnectionPoolDataSource-Members.md)   
 [SQLServerConnectionPoolDataSource Class](../content/SQLServerConnectionPoolDataSource-Class.md)  
  
  