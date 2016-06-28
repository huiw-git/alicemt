---
title: setMaxRows Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.setMaxRows
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
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
# setMaxRows Method (SQLServerStatement)
  Sets the limit for the maximum number of rows that any [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object can contain to the given number.  
  
## Syntax  
  
```  
  
public final void setMaxRows(int max)  
```  
  
#### Parameters  
 *max*  
  
 An **int** that indicates the maximum number of rows, or 0 if there is no limit.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setMaxRows method is specified by the setMaxRows method in the java.sql.Statement interface.  
  
 This setMaxRows method has no effect for dynamic scrollable cursors. The application should use SELECT TOP N SQL syntax to limit the number of rows returned from potentially large result sets.  
  
 When the setMaxRows method is called, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] executes the SET ROWCOUNT SQL statement when it runs the application's query. This causes the JDBC driver to limit the maximum number of rows affected by all the [!INCLUDE[tsql](../content/includes/tsql_md.md)] statements executed by that query, not just the number of rows returned by that query. If the application needs to set a limit only on the top\-level [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object, it should use SELECT TOP N SQL syntax in the query instead of the setMaxRows method.  
  
 For more information about the SET ROWCOUNT SQL statement, see the "[SET ROWCOUNT \(Transact\-SQL\)](http://go.microsoft.com/fwlink/?LinkId=139522)" topic in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  