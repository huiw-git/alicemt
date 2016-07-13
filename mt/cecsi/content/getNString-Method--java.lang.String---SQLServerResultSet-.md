---
title: getNString Method (java.lang.String) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 546d77e2-723a-42ac-ba3f-fabf2395d376
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
# getNString Method (java.lang.String) (SQLServerResultSet)
  Retrieves the value of the designated column in the current row of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.lang.String object.  
  
## Syntax  
  
```  
  
public java.lang.String getNString(java.lang.String columnLabel)  
```  
  
#### Parameters  
 *columnLabel*  
  
 A String that contains the column label.  
  
## Return Value  
 A String object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getNString method is specified by the getNString method in the java.sql.SQLServerResultSet interface.  
  
 This method can be used to retrieve the value of an **nvarchar**, **nchar**, **nvarchar\(max\)**, **ntext**, or **xml** column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object. If you try to use this method to retrieve values of other data types, an exception will be thrown.  
  
## See Also  
 [getNString Method &#40;SQLServerResultSet&#41;](../content/getNString-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)  
  
  