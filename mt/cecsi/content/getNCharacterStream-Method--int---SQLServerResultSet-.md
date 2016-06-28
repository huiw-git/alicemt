---
title: getNCharacterStream Method (int) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f1cfa4e4-3e1f-4504-b0de-cc626d653661
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
# getNCharacterStream Method (int) (SQLServerResultSet)
  Retrieves the value of a designated column in the current row of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a Reader object.  
  
## Syntax  
  
```  
  
public java.io.Reader getNCharacterStream(int columnIndex)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 A Reader object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getNCharacterStream method is specified by the getNCharacterStream method in the java.sql.ResultSet interface.  
  
 This method can be used to retrieve the value of an **nvarchar**, **nchar**, **nvarchar\(max\)**, **ntext**, or **xml** column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object. If you try to use this method to retrieve values of other data types, an exception will be thrown.  
  
## See Also  
 [getNCharacterStream Method &#40;SQLServerResultSet&#41;](../content/getNCharacterStream-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)  
  
  