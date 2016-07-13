---
title: Connection Pooling (Microsoft Drivers for PHP for SQL Server)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
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
  - zh-cn
  - zh-tw
---
# Connection Pooling (Microsoft Drivers for PHP for SQL Server)
The following are important points to note about connection pooling in the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]:  
  
-   The [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] uses ODBC connection pooling.  
  
-   By default, connection pooling is enabled. When you connect to a server, the driver attempts to use a pooled connection before it creates a new one. If an equivalent connection is not found in the pool, a new connection is created and added to the pool. The driver determines whether connections are equivalent based on a comparison of connection strings.  
  
-   When a connection from the pool is used, the connection state is reset.  
  
-   Closing the connection returns the connection to the pool.  
  
For more information about connection pooling, see [Driver Manager Connection Pooling](http://go.microsoft.com/fwlink/?linkid=119622).  
  
## Connection Attributes  
You can force the driver to create a new connection \(instead of looking for an equivalent connection in the connection pool\) by setting the value of the *ConnectionPooling* attribute in the connection string to **false** \(or 0\).  
  
If the *ConnectionPooling* attribute is omitted from the connection string or if it is set to **true** \(or 1\), the driver will only create a new connection if an equivalent connection does not exist in the connection pool.  
  
For information about other connection attributes, see [Connection Options](../content/Connection-Options.md).  
  
## See Also  
[How to: Connect Using Windows Authentication](../Topic/How%20to:%20Connect%20Using%20Windows%20Authentication.md)  
[How to: Connect Using SQL Server Authentication](../Topic/How%20to:%20Connect%20Using%20SQL%20Server%20Authentication.md)  
  
