---
title: "SQLServerPreparedStatement Class"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
caps.latest.revision: 15
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
# SQLServerPreparedStatement Class
  Represents the basic implementation of JDBC prepared statement functionality.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** SQLServerStatement  
  
 **Implements:** [ISQLServerPreparedStatement](../content/ISQLServerPreparedStatement-Interface.md)  
  
## Syntax  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## Remarks  
 SQLServerPreparedStatement provides methods that let you supply parameters as any native Java type and many Java object types. SQLServerPreparedStatement prepares a statement by using the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **sp_prepare** stored procedure, and then reuses the returned statement handle for each subsequent running of the statement, typically using different parameters provided by the user.  
  
 SQLServerPreparedStatement supports batching, where a set of prepared statements are run in a single database round trip, to improve runtime performance.  
  
 This class supports unwrapping to SQLServerPreparedStatement class, ISQLServerPreparedStatement interface, java.sql.PreparedStatement interface, and the classes and interfaces supported by SQLServerStatement for unwrapping. For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  