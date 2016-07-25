---
title: "isSparseColumnSet Method (SQLServerResultSetMetaData)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
caps.latest.revision: 7
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
# isSparseColumnSet Method (SQLServerResultSetMetaData)
  Indicates if a column in a result set is a sparse column set.  
  
## Syntax  
  
```scr  
public boolean isSparseColumnSet(int column)  
```  
  
#### Parameters  
 *column*  
  
 The (one-based) index of the column.  
  
## Return Value  
 **true** if a column in a result set is a sparse column set, otherwise **false**.  
  
## Remarks  
 This method does not retrieve information from the database.  
  
## See Also  
 [SQLServerResultSetMetaData Methods](../content/SQLServerResultSetMetaData-Methods.md)   
 [SQLServerResultSetMetaData Members](../content/SQLServerResultSetMetaData-Members.md)   
 [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md)  
  
  