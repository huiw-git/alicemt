---
title: SQLServerException Class
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
manager:jhubbard
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
# SQLServerException Class
  Represents an unsuccessful or incomplete running of an SQL statement.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.sql.SQLException  
  
 **Implements:** java.io.Serializable  
  
## Syntax  
  
```  
  
public final class SQLServerException  
```  
  
## Remarks  
 The SQLServerException class handles both SQL 92 and XOPEN state codes. They are switchable by using a user\-specified connection property. Exceptions are written to any open log files that have been specified.  
  
## See Also  
 [SQLServerException Members](../content/SQLServerException-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  