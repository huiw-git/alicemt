---
title: relative Method (SQLServerResultSet)
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
  - SQLServerResultSet.relative
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
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
# relative Method (SQLServerResultSet)
  Moves the cursor the given amount of rows, relative to the current row, in either a positive or negative direction.  
  
## Syntax  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### Parameters  
 *nRows*  
  
 An **int** that indicates the number of rows to move.  
  
## Return Value  
 **true** if the cursor is on a row. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This relative method is specified by the relative method in the java.sql.ResultSet interface.  
  
 Trying to move beyond the first or last row in the result set positions the cursor before or after the first or last row. Calling `relative(0)` is valid, but does not change the cursor position.  
  
 Calling the method `relative(1)` is identical to calling the [next](../content/next-Method--SQLServerResultSet-.md) method. Calling the method `relative(-1)` is identical to calling the [previous](../content/previous-Method--SQLServerResultSet-.md) method.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  