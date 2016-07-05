---
title: getBigDecimal Method (int, int) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getBigDecimal (int, int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: c99d0772-b26c-492c-a643-2813b5429993
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
# getBigDecimal Method (int, int) (SQLServerResultSet)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object using the given scale.  
  
> [!NOTE]  
>  This method has been deprecated from the JDBC specification. Instead, you should use the [getBigDecimal \(int\)](../content/getBigDecimal-Method--int---SQLServerResultSet-.md) method.  
  
## Syntax  
  
```  
  
public java.math.BigDecimal getBigDecimal(int columnIndex,  
                                          int scale)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
 *scale*  
  
 An **int** that indicates the number of digits to the right of the decimal point.  
  
## Return Value  
 A BigDecimal object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getBigDecimal method is specified by the getBigDecimal method in the java.sql.ResultSet interface.  
  
## See Also  
 [getBigDecimal Method &#40;SQLServerResultSet&#41;](../content/getBigDecimal-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  