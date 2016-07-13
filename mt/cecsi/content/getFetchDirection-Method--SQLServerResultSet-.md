---
title: getFetchDirection Method (SQLServerResultSet)
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
  - SQLServerResultSet.getFetchDirection
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
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
# getFetchDirection Method (SQLServerResultSet)
  Retrieves the fetch direction for this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public int getFetchDirection()  
```  
  
## Return Value  
 An **int** that indicates the current fetch direction.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getFetchDirection method is specified by the getFetchDirection method in the java.sql.ResultSet interface.  
  
 This method returns FETCH\_FORWARD for forward\-only cursors, the last setting made by a call to the [setFetchDirection](../content/setFetchDirection-Method--SQLServerResultSet-.md) method for other cursor types, and will return FETCH\_UNKNOWN these cursor types if the setFetchDirection method has never been called.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  