---
title: setFetchSize Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.setFetchSize
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
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
# setFetchSize Method (SQLServerResultSet)
  Gives the JDBC driver a hint as to the number of rows that should be fetched from the database when more rows are needed for this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### Parameters  
 *rows*  
  
 An **int** indicating the number of rows to fetch.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setFetchSize method is specified by the setFetchSize method in the java.sql.ResultSet interface.  
  
 If the fetch size specified is zero, the JDBC driver ignores the value and estimates what the fetch size should be. The default value is set by the [SQLServerStatement](../content/SQLServerStatement-Class.md) object that created the result set. The fetch size can be changed at any time.  
  
 This method changes the block fetch size for server cursors, and takes effect the next time the JDBC driver needs to call sp\_cursorfetch. Setting the fetch size to zero restores the default fetch size for the cursor type that is currently in use  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  