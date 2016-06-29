---
title: getQueryTimeout Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.getQueryTimeout
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
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
# getQueryTimeout Method (SQLServerStatement)
  Retrieves the number of seconds [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will wait for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object to run.  
  
## Syntax  
  
```  
  
public final int getQueryTimeout()  
```  
  
## Return Value  
 An **int** that indicates the number of seconds that the JDBC driver will wait, or 0 if there is no limit.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getQueryTimeout method is specified by the getQueryTimeout method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  