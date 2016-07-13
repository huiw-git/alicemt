---
title: setTransactionIsolation Method (SQLServerConnection)
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
  - SQLServerConnection.setTransactionIsolation
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 6a8fa4d3-5237-40f8-8a02-b40a3d7a1131
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
# setTransactionIsolation Method (SQLServerConnection)
  Tries to change the transaction isolation level for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object to the one given.  
  
## Syntax  
  
```  
  
public void setTransactionIsolation(int level)  
```  
  
#### Parameters  
 *level*  
  
 An **int** value that contains one of the following isolation levels:  
  
 TRANSACTION\_READ\_UNCOMMITTED  
  
 TRANSACTION\_READ\_COMMITTED  
  
 TRANSACTION\_REPEATABLE\_READ  
  
 TRANSACTION\_SERIALIZABLE  
  
 TRANSACTION\_SNAPSHOT \= 0x1000  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setTransactionIsolation method is specified by the setTransactionIsolation method in the java.sql.Connection interface.  
  
 Transactions are not committed if this method is called in the middle of a transaction.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  