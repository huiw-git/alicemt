---
title: getTransactionIsolation Method (SQLServerConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.getTransactionIsolation
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 179772e9-6572-4ce5-83c5-ab2b196cee67
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
# getTransactionIsolation Method (SQLServerConnection)
  Retrieves the current transaction isolation level of this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
## Syntax  
  
```  
  
public int getTransactionIsolation()  
```  
  
## Return Value  
 An **int** value that contains one of the following isolation levels:  
  
 TRANSACTION\_NONE  
  
 TRANSACTION\_READ\_UNCOMMITTED  
  
 TRANSACTION\_READ\_COMMITTED  
  
 TRANSACTION\_REPEATABLE\_READ  
  
 TRANSACTION\_SERIALIZABLE  
  
 TRANSACTION\_SNAPSHOT \= 0x1000  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getTransactionIsolation method is specified by the getTransactionIsolation method in the java.sql.Connection interface.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  