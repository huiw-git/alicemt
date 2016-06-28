---
title: getDate Method (int) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getDate (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: e6b6cfe2-b7c4-4d41-8e09-c68b5086a503
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
# getDate Method (int) (SQLServerResultSet)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Date object in the Java programming language.  
  
## Syntax  
  
```  
  
public java.sql.Date getDate(int columnIndex)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 A Date object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getDate method is specified by the getDate method in the java.sql.ResultSet interface.  
  
 This method returns a valid date part of a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] datetime or smalldatetime data type, with the time part set to the Java time baseline of 00:00 \(midnight\).  
  
## See Also  
 [getDate Method &#40;SQLServerResultSet&#41;](../content/getDate-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  