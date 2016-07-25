---
title: "cancelRowUpdates Method (SQLServerResultSet)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.cancelRowUpdates
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 2ecacca4-f7bc-4f5d-886a-da7747fdccae
caps.latest.revision: 9
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
# cancelRowUpdates Method (SQLServerResultSet)
  Cancels the updates made to the current row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public void cancelRowUpdates()  
```  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This cancelRowUpdates method is specified by the cancelRowUpdates method in the java.sql.ResultSet interface.  
  
 This method can be called after calling an updater method and before calling the [updateRow](../content/updateRow-Method--SQLServerResultSet-.md) method to roll back the updates that were made to a row. If no updates have been made or updateRow has already been called, this method has no effect.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  