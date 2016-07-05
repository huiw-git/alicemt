---
title: getColumnDisplaySize Method (SQLServerResultSetMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSetMetaData.getColumnDisplaySize
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 21c25443-bd2b-4b60-9798-4efe2c158952
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
# getColumnDisplaySize Method (SQLServerResultSetMetaData)
  Returns the normal maximum width, in characters, for the designated column.  
  
## Syntax  
  
```  
  
public int getColumnDisplaySize(int column)  
```  
  
#### Parameters  
 *column*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 An **int** that indicates the maximum width. If the width is not known, returns 0.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getColumnDisplaySize method is specified by the getColumnDisplaySize method in the java.sql.ResultSetMetaData interface.  
  
 [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0 has behavior changes in the COLUMN\_SIZE column. See [SQLServerDatabaseMetaData.getColumns](../content/getColumns-Method--SQLServerDatabaseMetaData-.md) for more information.  
  
## See Also  
 [SQLServerResultSetMetaData Members](../content/SQLServerResultSetMetaData-Members.md)   
 [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md)  
  
  