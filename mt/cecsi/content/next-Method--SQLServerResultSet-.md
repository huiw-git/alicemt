---
title: next Method (SQLServerResultSet)
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
  - SQLServerResultSet.next
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
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
# next Method (SQLServerResultSet)
  Moves the cursor down one row from its current position.  
  
## Syntax  
  
```  
  
public boolean next()  
```  
  
## Return Value  
 **true** if the new current row is valid. **false** if there are no more rows to process.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This next method is specified by the next method in the java.sql.ResultSet interface.  
  
 A result set cursor is initially positioned before the first row. The first call to the next method makes the first row the current row, the second call makes the second row the current row, and so on.  
  
 If an input stream is open for the current row, a call to the next method will implicitly close it. A warning chain for the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object is cleared when a new row is read.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  