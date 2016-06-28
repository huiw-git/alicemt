---
title: SQLServerXAConnection Class
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
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
# SQLServerXAConnection Class
  Represents JDBC connections that can participate in distributed \(XA\) transactions.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md)  
  
 **Implements:** javax.sql.XAConnection  
  
## Syntax  
  
```  
  
public class SQLServerXAConnection  
```  
  
## Remarks  
 A SQLServerXAConnection object can be enlisted in a distributed transaction by means of an [SQLServerXAResource](../content/SQLServerXAResource-Class.md) object. A transaction manager, usually part of a middle tier server, manages a SQLServerXAConnection object through the SQLServerXAResource object.  
  
> [!NOTE]  
>  Application programmers typically do not use this interface directly. It is primarily used by a transaction manager working in the middle tier server.  
  
## See Also  
 [SQLServerXAConnection Members](../content/SQLServerXAConnection-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  