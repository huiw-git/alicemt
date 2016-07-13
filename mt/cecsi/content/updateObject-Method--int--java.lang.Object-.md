---
title: updateObject Method (int, java.lang.Object)
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
  - SQLServerResultSet.updateObject (int, java.lang.Object)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4993dfe1-2232-4b3c-b931-dfdb35dd225a
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
# updateObject Method (int, java.lang.Object)
  Updates the designated column with an **Object** value given the column index.  
  
## Syntax  
  
```  
  
public void updateObject(int index,  
                         java.lang.Object obj)  
```  
  
#### Parameters  
 *index*  
  
 An **int** that indicates the column index.  
  
 *obj*  
  
 An **Object** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This updateObject method is specified by the updateObject method in the java.sql.ResultSet interface.  
  
## See Also  
 [updateObject Method &#40;SQLServerResultSet&#41;](../content/updateObject-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  