---
title: getBlob Method (int) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getBlob (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: a00275cb-0299-4a21-a518-2640598a5bbf
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
# getBlob Method (int) (SQLServerResultSet)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a Blob object in the Java programming language.  
  
## Syntax  
  
```  
  
public java.sql.Blob getBlob(int i)  
```  
  
#### Parameters  
 *i*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 A Blob object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getBlob method is specified by the getBlob method in the java.sql.ResultSet interface.  
  
## See Also  
 [getBlob Method &#40;SQLServerResultSet&#41;](../content/getBlob-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  