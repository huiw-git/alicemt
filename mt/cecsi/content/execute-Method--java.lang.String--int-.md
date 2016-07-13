---
title: execute Method (java.lang.String, int)
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
  - SQLServerStatement.execute (java.lang.String.int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: c8ea589e-5736-412d-9cd1-79bc4964f847
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
# execute Method (java.lang.String, int)
  Runs the given SQL statement, which can return multiple results, and signals to [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] that any auto\-generated keys should be made available for retrieval.  
  
## Syntax  
  
```  
  
public final boolean execute(java.lang.String sql,  
                             int flag)  
```  
  
#### Parameters  
 *sql*  
  
 A **String** that contains an SQL statement.  
  
 *flag*  
  
 An **int** value that indicates if auto\-generated keys should be made available. It must be one of the following constants:  
  
 RETURN\_GENERATED\_KEYS  
  
 NO\_GENERATED\_KEYS  
  
## Return Value  
 **true** if the first result is a result set. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This execute method is specified by the execute method in the java.sql.Statement interface.  
  
## See Also  
 [execute Method &#40;SQLServerStatement&#41;](../content/execute-Method--SQLServerStatement-.md)   
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  