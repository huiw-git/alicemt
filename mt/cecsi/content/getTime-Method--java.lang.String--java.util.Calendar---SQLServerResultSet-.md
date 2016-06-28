---
title: getTime Method (java.lang.String, java.util.Calendar) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getTime (java.lang.String, java.util.Calendar)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 13b51f77-cec9-45fc-862e-3d2bb2d718d7
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
# getTime Method (java.lang.String, java.util.Calendar) (SQLServerResultSet)
  Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Time object in the Java programming language, using the given Calendar object.  
  
## Syntax  
  
```  
  
public java.sql.Time getTime(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### Parameters  
 *colName*  
  
 A **String** that contains the column name.  
  
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
  
  