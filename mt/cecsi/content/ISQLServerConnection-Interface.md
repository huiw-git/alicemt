---
title: ISQLServerConnection Interface
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
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
# ISQLServerConnection Interface
  Represents a JDBC connection to a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database. This interface was added in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.sql.Connection  
  
## Syntax  
  
```  
  
public interface ISQLServerConnection  
```  
  
## Remarks  
 This interface is implemented by [SQLServerConnection Class](../content/SQLServerConnection-Class.md).  
  
 This interface exposes the following [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific field:  
  
|Field|For more information, see|  
|-----------|-------------------------------|  
|public final static int TRANSACTION\_SNAPSHOT|[TRANSACTION\_SNAPSHOT](../content/TRANSACTION_SNAPSHOT-Field--SQLServerConnection-.md)|  
|public UUID getClientConnectionId\(\)|[getClientConnectionID\(\)](../content/getClientConnectionID-Method--SQLServerConnection-.md)|  
  
## See Also  
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  