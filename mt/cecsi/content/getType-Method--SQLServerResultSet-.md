---
title: getType Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getType
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ffbc4a02-e851-431c-bc1a-7ab381d982bb
manager:jhubbard
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
# getType Method (SQLServerResultSet)
  Retrieves the cursor type of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public int getType()  
```  
  
## Return Value  
 An **int** that indicates the current cursor type, which can be one of the following values:  
  
 ResultSet.TYPE\_FORWARD\_ONLY  
  
 ResultSet.TYPE\_SCROLL\_INSENSITIVE  
  
 ResultSet.TYPE\_SCROLL\_SENSITIVE  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getType method is specified by the getType method in the java.sql.ResultSet interface.  
  
 This method can be used to determine the actual cursor type. If the application selected TYPE\_FORWARD\_ONLY or used a default cursor type, TYPE\_FORWARD\_ONLY will be returned.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  