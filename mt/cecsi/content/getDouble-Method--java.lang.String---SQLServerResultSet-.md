---
title: getDouble Method (java.lang.String) (SQLServerResultSet)
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
  - SQLServerResultSet.getDouble (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 3ee26412-43d2-404b-bc05-ffd0fc75805c
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
# getDouble Method (java.lang.String) (SQLServerResultSet)
  Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **double** in the Java programming language.  
  
## Syntax  
  
```  
  
public double getDouble(java.lang.String columnName)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
## Return Value  
 A **double** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getDouble method is specified by the getDouble method in the java.sql.ResultSet interface.  
  
 This method returns all number\-based data types with Java **double** fidelity.  
  
## See Also  
 [getDouble Method &#40;SQLServerResultSet&#41;](../content/getDouble-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  