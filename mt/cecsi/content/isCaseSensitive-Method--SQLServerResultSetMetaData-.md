---
title: isCaseSensitive Method (SQLServerResultSetMetaData)
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
  - SQLServerResultSetMetaData.isCaseSensitive
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4db67eb7-7ff2-4fb8-8052-39f699de53ff
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
# isCaseSensitive Method (SQLServerResultSetMetaData)
  Indicates whether a column is case\-sensitive.  
  
## Syntax  
  
```  
  
public boolean isCaseSensitive(int column)  
```  
  
#### Parameters  
 *column*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 **true** if the column is case sensitive. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isCaseSensitive method is specified by the isCaseSensitive method in the java.sql.ResultSetMetaData interface.  
  
## See Also  
 [SQLServerResultSetMetaData Methods](../content/SQLServerResultSetMetaData-Methods.md)   
 [SQLServerResultSetMetaData Members](../content/SQLServerResultSetMetaData-Members.md)   
 [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md)  
  
  