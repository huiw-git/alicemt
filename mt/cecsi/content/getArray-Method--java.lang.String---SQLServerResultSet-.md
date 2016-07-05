---
title: getArray Method (java.lang.String) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getArray java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: a98d159b-1fae-482a-9465-5411ce60f901
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
# getArray Method (java.lang.String) (SQLServerResultSet)
  Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as an Array object.  
  
## Syntax  
  
```  
  
public java.sql.Array getArray(java.lang.String colName)  
```  
  
#### Parameters  
 *colName*  
  
 A **String** that contains the column name.  
  
## Return Value  
 An Array object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getArray method is specified by the getArray method in the java.sql.ResultSet interface.  
  
## See Also  
 [getArray Method &#40;SQLServerResultSet&#41;](../content/getArray-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  