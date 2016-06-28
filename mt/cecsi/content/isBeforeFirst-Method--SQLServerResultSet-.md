---
title: isBeforeFirst Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.isBeforeFirst
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: e0e2bd28-6949-47dc-b9dd-145ffb337069
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
# isBeforeFirst Method (SQLServerResultSet)
  Retrieves whether the cursor is before the first row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public boolean isBeforeFirst()  
```  
  
## Return Value  
 **true** if the cursor is before the first row. **false** if the cursor is at any other position or if the result set contains no rows.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isBeforeFirst method is specified by the isBeforeFirst method in the java.sql.ResultSet interface.  
  
 If this method is used with dynamic cursors, including forward\-only read\-only cursors, and the selectMethod connection property is set to "cursor", an exception will occur.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  