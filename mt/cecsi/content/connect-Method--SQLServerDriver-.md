---
title: "connect Method (SQLServerDriver)"
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
  - SQLServerDriver.connect
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 43813a4c-1cc7-4659-ba27-f1786f1371eb
caps.latest.revision: 7
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
# connect Method (SQLServerDriver)
  Makes a connection to the database.  
  
## Syntax  
  
```  
  
public java.sql.Connection connect(java.lang.String Url,  
                                   java.util.Properties suppliedProperties)  
```  
  
#### Parameters  
 *Url*  
  
 A **String** value that contains the URL that is used to connect to the database.  
  
 *suppliedProperties*  
  
 A set of string value pairs used as connection arguments.  
  
## Return Value  
 A Connection object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This connect method is specified by the connect method in the java.sql.Driver interface.  
  
## See Also  
 [SQLServerDriver Methods](../content/SQLServerDriver-Methods.md)   
 [SQLServerDriver Members](../content/SQLServerDriver-Members.md)   
 [SQLServerDriver Class](../content/SQLServerDriver-Class.md)  
  
  