---
title: getMaxRows Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.getMaxRows
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
manager:jhubbard
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
# getMaxRows Method (SQLServerStatement)
  Retrieves the maximum number of rows that a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object that is produced by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object can contain.  
  
## Syntax  
  
```  
  
public final int getMaxRows()  
```  
  
## Return Value  
 An **int** that indicates the maximum number of rows, or 0 if there is no limit.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getMaxRows method is specified by the getMaxRows method in the java.sql.Statement interface.  
  
 This getMaxRows method always returns 0 for dynamic scrollable cursors.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  