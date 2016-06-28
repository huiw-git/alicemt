---
title: ISQLServerStatement Interface
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f83b514-6e76-4f37-baf3-a10db2010e7c
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
# ISQLServerStatement Interface
  Represents the basic implementation of JDBC statement functionality. This interface was added in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.sql.Statement  
  
## Syntax  
  
```  
  
public interface ISQLServerStatement  
```  
  
## Remarks  
 This interface is implemented by [SQLServerStatement Class](../content/SQLServerStatement-Class.md).  
  
 This interface exposes the following [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific methods:  
  
|Method|For more information, see|  
|------------|-------------------------------|  
|public String getResponseBuffering|[getResponseBuffering](../content/getResponseBuffering-Method--SQLServerStatement-.md)|  
|public void setResponseBuffering|[setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md)|  
  
## See Also  
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  