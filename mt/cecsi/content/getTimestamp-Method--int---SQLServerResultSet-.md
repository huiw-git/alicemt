---
title: getTimestamp Method (int) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getTimestamp (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ad538a76-983f-4175-9481-9e7fa9480c71
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
# getTimestamp Method (int) (SQLServerResultSet)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Timestamp object in the Java programming language.  
  
## Syntax  
  
```  
  
public java.sql.Timestamp getTimestamp(int columnIndex)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
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
  
  