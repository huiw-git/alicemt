---
title: getTime Method (int, java.util.Calendar) (SQLServerResultSet)
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
  - SQLServerResultSet.getTime (int, java.util.Calendar)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d21e0c1d-9d6e-468f-8b11-cc7209b2c2e5
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
# getTime Method (int, java.util.Calendar) (SQLServerResultSet)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Time object in the Java programming language, using the given Calendar object.  
  
## Syntax  
  
```  
  
public java.sql.Time getTime(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
 *cal*  
  
 A Calendar object.  
  
## Return Value  
 A Time object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getTime method is specified by the getTime method in the java.sql.ResultSet interface.  
  
 This method returns a valid time part of a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] datetime or smalldatetime data type, with the date part set to the Java baseline date of 1970\/01\/01 in the supplied Calendar's timezone.  
  
## See Also  
 [getTime Method &#40;SQLServerResultSet&#41;](../content/getTime-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  