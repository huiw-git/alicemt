---
title: Performing Transactions with the JDBC Driver
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
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
# Performing Transactions with the JDBC Driver
  Transaction processing is a mandatory requirement of all applications that must guarantee consistency of their persistent data. With the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], transaction processing can either be performed locally or distributed. Transactions are atomic, consistent, isolated, and durable \(ACID\) modules of execution.  
  
 The topics in this section describe how the JDBC driver supports transactions including isolation levels, transaction savepoints, and result set holdability.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Understanding Transactions](../content/Understanding-Transactions.md)|Provides an overview of how transactions are used with the JDBC driver.|  
|[Understanding XA Transactions](../content/Understanding-XA-Transactions.md)|Provides an overview of how XA transactions are used with the JDBC driver.|  
|[Understanding Isolation Levels](../content/Understanding-Isolation-Levels.md)|Describes the various isolation levels that are supported by the JDBC driver.|  
|[Using Savepoints](../content/Using-Savepoints.md)|Describes how to use the JDBC driver with transaction savepoints.|  
|[Using Holdability](../content/Using-Holdability.md)|Describes how to use the JDBC driver with result set holdability.|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  