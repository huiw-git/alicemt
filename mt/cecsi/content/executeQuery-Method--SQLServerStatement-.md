---
title: executeQuery Method (SQLServerStatement)
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
  - SQLServerStatement.executeQuery
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 599cf463-e19f-4baa-bacb-513cad7c6cd8
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
# executeQuery Method (SQLServerStatement)
  Runs the given SQL statement and returns a single [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### Parameters  
 *sql*  
  
 A **String** that contains an SQL statement.  
  
## Return Value  
 A SQLServerResultSet object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This executeQuery method is specified by the executeQuery method in the java.sql.Statement interface.  
  
 [SQLServerException](../content/SQLServerException-Class.md) is thrown if the given SQL statement produces anything other than a single [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
 If executing a stored procedure results in an update count that is greater than one, or that generates more than one result set, use the [execute](../content/execute-Method--SQLServerStatement-.md) method to execute the stored procedure.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  