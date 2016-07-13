---
title: getTimestamp Method (java.lang.String) (SQLServerResultSet)
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
  - SQLServerResultSet.getTimestamp (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8b3c3938-e057-4919-9e9f-01eb8a4ad937
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
# getTimestamp Method (java.lang.String) (SQLServerResultSet)
  Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Timestamp object in the Java programming language.  
  
## Syntax  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String columnName)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
## Return Value  
 A Timestamp object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getTimestamp method is specified by the getTimestamp method in the java.sql.ResultSet interface.  
  
 This method returns values only from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] datetime and smalldatetime columns.  
  
## See Also  
 [getTimestamp Method &#40;SQLServerResultSet&#41;](../content/getTimestamp-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  