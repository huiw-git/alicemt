---
title: isAutoIncrement Method (SQLServerResultSetMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSetMetaData.isAutoIncrement
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 028b8d61-9557-4c9f-b732-29e87a962de8
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
# isAutoIncrement Method (SQLServerResultSetMetaData)
  Indicates whether the designated column is automatically numbered, which makes it read\-only.  
  
## Syntax  
  
```  
  
public boolean isAutoIncrement(int column)  
```  
  
#### Parameters  
 *column*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 **true** if the column is automatically numbered. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isAutoIncrement method is specified by the isAutoIncrement method in the java.sql.ResultSetMetaData interface.  
  
## See Also  
 [SQLServerResultSetMetaData Methods](../content/SQLServerResultSetMetaData-Methods.md)   
 [SQLServerResultSetMetaData Members](../content/SQLServerResultSetMetaData-Members.md)   
 [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md)  
  
  