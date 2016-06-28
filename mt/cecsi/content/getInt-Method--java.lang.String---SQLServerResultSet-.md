---
title: getInt Method (java.lang.String) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getInt (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 76b7054d-46dd-4d87-93a4-a7ea2ae9b7fd
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
# getInt Method (java.lang.String) (SQLServerResultSet)
  Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as an **int** in the Java programming language.  
  
## Syntax  
  
```  
  
public int getInt(java.lang.String columnName)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
## Return Value  
 An **int** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getInt method is specified by the getInt method in the java.sql.ResultSet interface.  
  
 This method is supported only on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types that can safely return an integer value such as int, smallint, tinyint, and bit. Using this method on any other data types will cause an exception to be thrown.  
  
## See Also  
 [getInt Method &#40;SQLServerResultSet&#41;](../content/getInt-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  