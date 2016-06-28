---
title: updateNClob Method (int, java.sql.NClob)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e9bca18-f64e-46a4-8541-2c9c39b393b5
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
# updateNClob Method (int, java.sql.NClob)
  Updates the designated column with a **NClob** value.  
  
## Syntax  
  
```  
  
public void updateNClob(int columnIndex,  
                        java.sql.NClob nClob)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
 *nClob*  
  
 An NClob object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This updateNClob method is specified by the updateNClob method in the java.sql.ResultSet interface.  
  
 This method is supported only on **nvarchar\(max\)**, **ntext**, and **xml** columns. Using this method on any other data types will cause an exception to be thrown.  
  
## See Also  
 [updateNClob Method &#40;SQLServerResultSet&#41;](../content/updateNClob-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  