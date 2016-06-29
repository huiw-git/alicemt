---
title: SQLServerStatement Class
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
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
# SQLServerStatement Class
  Represents the basic implementation of JDBC statement functionality.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Implements:** [ISQLServerStatement](../content/ISQLServerStatement-Interface.md)  
  
## Syntax  
  
```  
  
public class SQLServerStatement  
```  
  
## Remarks  
 The SQLServerStatement class also provides a number of base class implementation methods for the JDBC prepared statement and callable statements. The basic role of the SQLServerStatement class is to run SQL statements, and then return update counts and result sets to the user application.  
  
 This class supports unwrapping to SQLServerStatement class, the ISQLServerStatement interface, and the java.sql.Statement interface. For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  