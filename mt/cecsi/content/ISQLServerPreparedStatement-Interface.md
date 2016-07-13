---
title: ISQLServerPreparedStatement Interface
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf87892e-5c34-4ac6-8258-c2a81e117b26
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
# ISQLServerPreparedStatement Interface
  Represents the basic implementation of JDBC prepared statement functionality. This interface was added in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.sql.PreparedStatement, [ISQLServerStatement](../content/ISQLServerStatement-Interface.md)  
  
## Syntax  
  
```  
  
public interface ISQLServerPreparedStatement  
```  
  
## Remarks  
 This interface is implemented by [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md).  
  
 This interface exposes the following [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific methods:  
  
|Method|For more information, see|  
|------------|-------------------------------|  
|public void setDateTimeOffset\(int, microsoft.sql.DateTimeOffset\)|[setDateTimeOffset](../content/setDateTimeOffset-Method--SQLServerPreparedStatement-.md)|  
  
## See Also  
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  