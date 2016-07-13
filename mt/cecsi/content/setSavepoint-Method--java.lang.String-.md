---
title: setSavepoint Method (java.lang.String)
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
  - SQLServerConnection.setSavepoint (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 1cf15ec4-d9d9-4ab3-bfee-2ea43ff609a6
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
# setSavepoint Method (java.lang.String)
  Creates a savepoint with the given name in the current transaction, and returns the new [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object that represents it.  
  
## Syntax  
  
```  
  
public java.sql.Savepoint setSavepoint(java.lang.String sName)  
```  
  
#### Parameters  
 *sName*  
  
 A **String** value that contains the name of the savepoint.  
  
## Return Value  
 A SavePoint object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setSavePoint method is specified by the setSavePoint method in the java.sql.Connection interface.  
  
 The *sName* argument is automatically escaped by the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)].  
  
## See Also  
 [setSavepoint Method &#40;SQLServerConnection&#41;](../content/setSavepoint-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  