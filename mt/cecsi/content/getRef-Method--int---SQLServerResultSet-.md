---
title: getRef Method (int) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getRef (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: fc3f2d79-7cc3-47fa-a05e-4f7939d7f090
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
# getRef Method (int) (SQLServerResultSet)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a Ref object in the Java programming language.  
  
## Syntax  
  
```  
  
public java.sql.Ref getRef(int i)  
```  
  
#### Parameters  
 *i*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 A Ref object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getRef method is specified by the getRef method in the java.sql.ResultSet interface.  
  
## See Also  
 [getRef Method &#40;SQLServerResultSet&#41;](../content/getRef-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  