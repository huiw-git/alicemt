---
title: executeUpdate Method (SQLServerStatement)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.executeUpdate
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 10ae662a-ce3c-4b24-875c-5c2df319d93b
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
# executeUpdate Method (SQLServerStatement)
  Runs the given SQL statement, which can be an INSERT, UPDATE, or DELETE statement; or an SQL statement that returns nothing, such as an SQL DDL statement. Beginning in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, executeUpdate will return the correct number of rows updated in a MERGE operation.  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[executeUpdate \(java.lang.String\)](../content/executeUpdate-Method--java.lang.String---SQLServerStatement-.md)|Runs the given SQL statement, which can be an INSERT, UPDATE, DELETE, or MERGE statement; or an SQL statement that returns nothing, such as an SQL DDL statement.|  
|[executeUpdate \(java.lang.String, int\)](../content/executeUpdate-Method--java.lang.String--int-.md)|Runs the given SQL statement and signals the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] with the given flag about whether the auto\-generated keys produced by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object should be made available for retrieval.|  
|[executeUpdate \(java.lang.String, int&#91;&#93;\)](../content/executeUpdate-Method--java.lang.String--int[]-.md)|Runs the given SQL statement and signals the JDBC driver that the auto\-generated keys that are indicated in the given array should be made available for retrieval.|  
|[executeUpdate \(java.lang.String, java.lang.String&#91;&#93;\)](../content/executeUpdate-Method--java.lang.String--java.lang.String-.md)|Runs the given SQL statement and signals the JDBC driver that the auto\-generated keys that are indicated in the given array should be made available for retrieval.|  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  