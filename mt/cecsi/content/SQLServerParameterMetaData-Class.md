---
title: SQLServerParameterMetaData Class
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
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
# SQLServerParameterMetaData Class
  Represents the metadata for prepared statement parameters.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.lang.Object  
  
 **Implements:** java.sql.ParameterMetaData  
  
## Syntax  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## Remarks  
 To retrieve parameter metadata, prepared statements are run with SET FMT ONLY. Callable statements call sp\_sproc\_columns to retrieve names and metadata for the procedure parameters.  
  
## See Also  
 [SQLServerParameterMetaData Members](../content/SQLServerParameterMetaData-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  