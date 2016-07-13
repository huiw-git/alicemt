---
title: moveToInsertRow Method (SQLServerResultSet)
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
  - SQLServerResultSet.moveToInsertRow
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
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
# moveToInsertRow Method (SQLServerResultSet)
  Moves the cursor to the insert row.  
  
## Syntax  
  
```  
  
public void moveToInsertRow()  
```  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This moveToInsertRow method is specified by the moveToInsertRow method in the java.sql.ResultSet interface.  
  
 The current cursor position is remembered while the cursor is positioned on the insert row. The insert row is a special row that is associated with an updatable result set. It is essentially a buffer where a new row can be constructed by calling the updater methods before adding the row to the result set.  
  
 Only the updater, getter, and [insertRow](../content/insertRow-Method--SQLServerResultSet-.md) methods can be called when the cursor is on the insert row. All the columns in a result set must be given a value each time this method is called, and before calling insertRow. An updater method must be called before a getter method can be called on a column value.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  