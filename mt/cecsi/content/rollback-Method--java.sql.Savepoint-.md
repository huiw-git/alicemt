---
title: rollback Method (java.sql.Savepoint)
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
  - SQLServerConnection.rollback (java.sql.Savepoint)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d5dbd9ef-194f-4130-bfcc-7901a4fa8ded
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
# rollback Method (java.sql.Savepoint)
  Undoes all changes made after the given [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object was set.  
  
## Syntax  
  
```  
  
public void rollback(java.sql.Savepoint s)  
```  
  
#### Parameters  
 *s*  
  
 The SavePoint object to rollback to.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This rollBack method is specified by the rollBack method in the java.sql.Connection interface.  
  
 This method should be used only when auto\-commit mode has been disabled.  
  
## See Also  
 [rollback Method &#40;SQLServerConnection&#41;](../content/rollback-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  