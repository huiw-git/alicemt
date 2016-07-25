---
title: "getConnection Method (SQLServerPooledConnection)"
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
  - SQLServerPooledConnection.getConnection
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 05bdb61f-26e8-480f-a1c1-1e46a8ed4b70
caps.latest.revision: 4
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
# getConnection Method (SQLServerPooledConnection)
  Creates an object handle for the physical connection that this [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md) object represents.  
  
## Syntax  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## Return Value  
 A Connection object.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getConnection method is specified by the getConnection method in the javax.sql.PooledConnection interface.  
  
## See Also  
 [SQLServerPooledConnection Methods](../content/SQLServerPooledConnection-Methods.md)   
 [SQLServerPooledConnection Members](../content/SQLServerPooledConnection-Members.md)   
 [SQLServerPooledConnection Class](../content/SQLServerPooledConnection-Class.md)  
  
  