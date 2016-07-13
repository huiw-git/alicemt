---
title: executeBatch Method (SQLServerPreparedStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.executeBatch
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8418167e-cbd2-464d-b118-73cdd76080ed
manager:jhubbard
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
# executeBatch Method (SQLServerPreparedStatement)
  Submits a batch of commands to the database to be run. If all commands run successfully, returns an array of update counts.  
  
## Syntax  
  
```  
  
public int[] executeBatch()  
```  
  
## Return Value  
 An array of ints that contains the update counts.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
 java.sql.BatchUpdateException  
  
## Remarks  
 This executeBatch method is specified by the executeBatch method in the java.sql.Statement interface.  
  
 The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0 is compliant with the JDBC 4.0 recommendation that a call to the CallableStatement.executeBatch method \(inherited from PreparedStatement\) will throw a BatchUpdateException if the stored procedure accepts OUT or INOUT parameters or returns something other than an update count.  
  
 This method overrides [SQLServerStatement.executeBatch](../content/executeBatch-Method--SQLServerStatement-.md).  
  
## See Also  
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  