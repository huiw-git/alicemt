---
title: getPooledConnection Method (java.lang.String, java.lang.String)
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
  - SQLServerConnectionPoolDataSource.getPooledConnection (java.lang.String, java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f2e6391d-9aaf-4b09-ae1c-a27c1ada6301
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
# getPooledConnection Method (java.lang.String, java.lang.String)
  Tries to establish a physical database connection that can be used as a pooled connection based on the given user name and password.  
  
## Syntax  
  
```  
  
public javax.sql.PooledConnection getPooledConnection(java.lang.String user,  
                                                      java.lang.String password)  
```  
  
#### Parameters  
 *user*  
  
 A **String** that contains the user name.  
  
 *passwword*  
  
 A **String** that contains the password.  
  
## Return Value  
 A [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md) object.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getPooledConnection method is specified by the getPooledConnection method in the javax.sql.ConnectionPoolDataSource interface.  
  
## See Also  
 [getPooledConnection](../content/getPooledConnection-Method--SQLServerConnectionPoolDataSource-.md)   
 [SQLServerConnectionPoolDataSource Methods](../content/SQLServerConnectionPoolDataSource-Methods.md)   
 [SQLServerConnectionPoolDataSource Members](../content/SQLServerConnectionPoolDataSource-Members.md)   
 [SQLServerConnectionPoolDataSource Class](../content/SQLServerConnectionPoolDataSource-Class.md)  
  
  