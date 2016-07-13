---
title: executeUpdate Method (java.lang.String) (SQLServerStatement)
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
  - SQLServerStatement.executeUpdate (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 85e7c3a2-f2da-49bf-9d90-5fd246fd60e1
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
# executeUpdate Method (java.lang.String) (SQLServerStatement)
  Runs the given SQL statement, which can be an INSERT, UPDATE, or DELETE statement; or an SQL statement that returns nothing, such as an SQL DDL statement. Beginning in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, executeUpdate will return the correct number of rows updated in a MERGE operation.  
  
## Syntax  
  
```  
  
public int executeUpdate(java.lang.String sql)  
```  
  
#### Parameters  
 *sql*  
  
 A **String** that contains the SQL statement.  
  
## Return Value  
 An **int** that indicates the number of rows affected, or 0 if using a DDL statement.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This executeUpdate method is specified by the executeUpdate method in the java.sql.Statement interface.  
  
 If executing a stored procedure results in an update count that is greater than one, or that generates more than one result set, use the [execute](../content/execute-Method--SQLServerStatement-.md) method to execute the stored procedure.  
  
## See Also  
 [executeUpdate Method &#40;SQLServerStatement&#41;](../content/executeUpdate-Method--SQLServerStatement-.md)   
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  