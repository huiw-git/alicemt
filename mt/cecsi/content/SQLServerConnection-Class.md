---
title: SQLServerConnection Class
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
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
# SQLServerConnection Class
  Represents a JDBC connection to a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Implements:** [ISQLServerConnection](../content/ISQLServerConnection-Interface.md), java.io.Serializable  
  
## Syntax  
  
```  
  
public class SQLServerConnection  
```  
  
## Remarks  
 SQLServerConnection supports JDBC connection pooling and can be either a physical JDBC connection or a logical JDBC connection. SQLServerConnection manages transaction control for all statements that were created from it, and it can participate in XA distributed transactions managed via a XAResource adapter.  
  
 SQLServerConnection manages a pool of prepared statement handles. Prepared statements are prepared once and are typically run many times with different data values for their parameters. Prepared statements are also maintained across logical \(pooled\) connection closes.  
  
> [!NOTE]  
>  SQLServerConnection is not thread safe. However, multiple statements that are created from a single connection can be processed simultaneously in concurrent threads.  
  
 This class supports unwrapping to SQLServerConnection class, java.sql.connection interface, and ISQLServerConnection interface. For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  