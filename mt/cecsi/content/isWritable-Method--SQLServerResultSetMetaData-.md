---
title: isWritable Method (SQLServerResultSetMetaData)
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
  - SQLServerResultSetMetaData.isWritable
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 50846aa8-e4e5-4fc3-a638-0e5fa8b597be
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
# isWritable Method (SQLServerResultSetMetaData)
  Indicates whether it is possible for a write on the designated column to succeed.  
  
## Syntax  
  
```  
  
public boolean isWritable(int column)  
```  
  
#### Parameters  
 *column*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 **true** if writes will succeed on the column. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isWritable method is specified by the isWritable method in the java.sql.ResultSetMetaData interface.  
  
## See Also  
 [SQLServerResultSetMetaData Methods](../content/SQLServerResultSetMetaData-Methods.md)   
 [SQLServerResultSetMetaData Members](../content/SQLServerResultSetMetaData-Members.md)   
 [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md)  
  
  