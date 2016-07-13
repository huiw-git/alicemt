---
title: Closing Objects when Not In Use
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
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
# Closing Objects when Not In Use
  When you work with objects of [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], particularly the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) or one of the Statement objects such as [SQLServerStatement](../content/SQLServerStatement-Class.md), [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) or [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md), you should explicitly close them by using their close methods when they are no longer needed. This improves performance by freeing up driver and server resources as soon as possible, instead of waiting for the Java Virtual Machine garbage collector to do it for you.  
  
 Closing objects is particularly crucial to maintaining good concurrency on the server when you are using scroll locks. Scroll locks in the last accessed fetch buffer are held until the result set is closed. Similarly, statement prepared handles are held until the statement is closed. If you are reusing a connection for multiple statements, closing the statements before you let them go out of scope will allow the server to clean up the prepared handles earlier.  
  
## See Also  
 [Improving Performance and Reliability with the JDBC Driver](../content/Improving-Performance-and-Reliability-with-the-JDBC-Driver.md)  
  
  