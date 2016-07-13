---
title: setSavepoint Method ()
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
  - SQLServerConnection.setSavepoint ()
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
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
# setSavepoint Method ()
  Creates an unnamed savepoint in the current transaction, and returns the new [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object that represents it.  
  
## Syntax  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## Return Value  
 A SavePoint object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setSavePoint method is specified by the setSavePoint method in the java.sql.Connection interface.  
  
## See Also  
 [setSavepoint Method &#40;SQLServerConnection&#41;](../content/setSavepoint-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  