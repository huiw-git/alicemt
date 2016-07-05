---
title: updateAsciiStream Method (java.lang.String, java.io.InputStream)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 747b0308-1ce6-4eba-bdfc-af29c21c18cf
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
# updateAsciiStream Method (java.lang.String, java.io.InputStream)
  Updates the designated column with an ASCII stream value.  
  
## Syntax  
  
```  
  
public void updateAsciiStream(java.lang.String columnLabel,  
                              java.io.InputStream x)  
```  
  
#### Parameters  
 *columnLabel*  
  
 A **String** that contains the column label.  
  
 *x*  
  
 An InputStream object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This updateAsciiStream method is specified by the updateAsciiStream method in the java.sql.ResultSet interface.  
  
 This method passes ASCII characters \(bytes\) from an InputStream object to convertible character columns, which are the ASCII range \[0x00 – 0x7F\] of Unicode, and 874, 932, 936, 949, 950, and 1250 through 1258 code pages. This method performs a conversion to the destination collation page. Trying to update an unconvertible destination column will cause an exception to be thrown. For binary columns, raw bytes are passed.  
  
 Using this method for the **image**, **text**, and **ntext**[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types might impact performance.  
  
## See Also  
 [updateAsciiStream Method &#40;SQLServerResultSet&#41;](../content/updateAsciiStream-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  