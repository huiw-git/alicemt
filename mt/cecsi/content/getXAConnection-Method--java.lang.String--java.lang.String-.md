---
title: getXAConnection Method (java.lang.String, java.lang.String)
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
  - SQLServerXADataSource.getXAConnection (java.lang.String, java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 276e0093-3d42-4f73-acc4-2b5b98245b40
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
# getXAConnection Method (java.lang.String, java.lang.String)
  Tries to establish a physical database connection using the given user name and password.  
  
## Syntax  
  
```  
  
public javax.sql.XAConnection getXAConnection(java.lang.String user,  
                                              java.lang.String password)  
```  
  
#### Parameters  
 *user*  
  
 A **String** that contains the user name.  
  
 *password*  
  
 A **String** that contains the password.  
  
## Return Value  
 An XAConnection object.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getXAConnection method is specified by the getXAConnection method in the javax.sql.XADataSource interface.  
  
> [!NOTE]  
>  This method is typically called by XA connection pool implementations and not by regular JDBC application code.  
  
## See Also  
 [getXAConnection Method &#40;SQLServerXADataSource&#41;](../content/getXAConnection-Method--SQLServerXADataSource-.md)   
 [SQLServerXADataSource Methods](../content/SQLServerXADataSource-Methods.md)   
 [SQLServerXADataSource Members](../content/SQLServerXADataSource-Members.md)   
 [SQLServerXADataSource Class](../content/SQLServerXADataSource-Class.md)  
  
  