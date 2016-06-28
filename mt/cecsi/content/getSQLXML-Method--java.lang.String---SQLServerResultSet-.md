---
title: getSQLXML Method (java.lang.String) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab9c7b10-026f-4a51-8d60-e6871d1abd02
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
# getSQLXML Method (java.lang.String) (SQLServerResultSet)
  Retrieves the value of a designated column in the current row of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a SQLXML object.  
  
## Syntax  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String columnLabel)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that indicates the column label.  
  
## Return Value  
 ASQLXMLobject.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getSQLXML method is specified by the getSQLXML method in the java.sql.ResultSet interface.  
  
## See Also  
 [getSQLXML Method &#40;SQLServerResultSet&#41;](../content/getSQLXML-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)  
  
  