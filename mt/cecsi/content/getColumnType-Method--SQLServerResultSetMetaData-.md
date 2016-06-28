---
title: getColumnType Method (SQLServerResultSetMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSetMetaData.getColumnType
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 81815a41-9265-4574-a4d8-f6341a68d9fd
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
# getColumnType Method (SQLServerResultSetMetaData)
  Retrieves the SQL type of the designated column.  
  
## Syntax  
  
```  
  
public int getColumnType(int column)  
```  
  
#### Parameters  
 *column*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 An **int** that indicates the JDBC type as defined in java.sql.Types.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getColumnType method is specified by the getColumnType method in the java.sql.ResultSetMetaData interface.  
  
 [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0 has behavior changes in the DATA\_TYPE column. See [SQLServerDatabaseMetaData.getColumns](../content/getColumns-Method--SQLServerDatabaseMetaData-.md) for more information.  
  
## See Also  
 [SQLServerResultSetMetaData Members](../content/SQLServerResultSetMetaData-Members.md)   
 [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md)  
  
  