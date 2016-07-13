---
title: SQLServerConnectionPoolDataSource Class
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
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
# SQLServerConnectionPoolDataSource Class
  Represents physical database connections for connection pool managers.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** [SQLServerDataSource](../content/SQLServerDataSource-Class.md)  
  
 **Implements:** javax.sql.ConnectionPoolDataSource  
  
## Syntax  
  
```  
  
public class SQLServerConnectionPoolDataSource  
```  
  
## Remarks  
 SQLServerConnectionPoolDataSource is typically used in Java Application Server environments that support built\-in connection pooling and require a ConnectionPoolDataSource to provide physical connections, such as Java Platform, Enterprise Edition \(Java EE\) application servers that provide JDBC 3.0 API spec connection pooling.  
  
## See Also  
 [SQLServerConnectionPoolDataSource Members](../content/SQLServerConnectionPoolDataSource-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  