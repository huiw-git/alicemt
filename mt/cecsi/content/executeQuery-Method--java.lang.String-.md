---
title: executeQuery Method (java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
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
# executeQuery Method (java.lang.String)
  Runs the given SQL statement and returns a single [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
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
  
 This method overrides the [executeQuery](../content/executeQuery-Method--SQLServerStatement-.md) method that is found in the [SQLServerStatement](../content/SQLServerStatement-Class.md) class.  
  
 Calling this method will result in an exception since the SQL statement for the SQLServerPreparedStatement object is specified when the object is created.  
  
 [SQLServerException](../content/SQLServerException-Class.md) is thrown if the given SQL statement produces anything other than a single [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## See Also  
 [executeQuery Method &#40;SQLServerPreparedStatement&#41;](../content/executeQuery-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  