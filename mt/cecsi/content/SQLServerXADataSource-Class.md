---
title: SQLServerXADataSource Class
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
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
# SQLServerXADataSource Class
  Represents a factory for [SQLServerXAConnection](../content/SQLServerXAConnection-Class.md) objects that is used internally.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** [SQLServerConnectionPoolDataSource](../content/SQLServerConnectionPoolDataSource-Class.md)  
  
 **Implements:** javax.sql.XADataSource  
  
## Syntax  
  
```  
  
public class SQLServerXADataSource  
```  
  
## Remarks  
 An object that implements the SQLServerXADataSource interface is typically registered with a naming service that uses the Java Naming and Directory Interface \(JNDI\).  
  
 The SQLServerXADataSource class provides database connections for use in distributed \(XA\) transactions. The SQLServerXADataSource class also supports connection pooling of physical connections. The SQLServerXADataSource and SQLServerXAConnection interfaces, which are defined in the package javax.sql, are implemented by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
 A SQLServerXAConnection object is a pooled connection that can participate in a distributed transaction. More precisely, SQLServerXAConnection extends the SQLServerPooledConnection interface by adding the method [getXAResource](../content/getXAResource-Method--SQLServerXAConnection-.md). This method produces a [SQLServerXAResource](../content/SQLServerXAResource-Class.md) object that can be used by a transaction manager to coordinate the work done on this connection with the other participants in the distributed transaction. Because they extend the SQLServerPooledConnection interface, SQLServerXAConnection objects support all the methods of SQLServerPooledConnection objects. They are reusable physical connections to an underlying data source and produce logical connection handles that can be passed back to a JDBC application.  
  
 SQLServerXAConnection objects are produced by a SQLServerXADataSource object. SQLServerConnectionPoolDataSource objects and SQLServerXADataSource objects are similar because they are both implemented below a data source layer that is visible to the JDBC application. This architecture lets [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] support distributed transactions in a way that is transparent to the application. SQLServerXADataSource can be configured to integrate with [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Distributed Transaction Coordinator \(DTC\) to provide true, distributed transaction processing.  
  
## See Also  
 [SQLServerXADataSource Members](../content/SQLServerXADataSource-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  