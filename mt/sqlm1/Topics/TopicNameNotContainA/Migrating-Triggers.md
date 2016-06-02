---
title: Migrating Triggers
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
---
# Migrating Triggers
  This topic discusses DDL triggers and memory\-optimized tables.  
  
 DML triggers are supported on memory\-optimized tables, but only with the FOR | AFTER trigger event.  
  
 LOGON triggers are triggers defined to fire on LOGON events. LOGON triggers do not affect memory\-optimized tables.  
  
## DDL Triggers  
 DDL triggers are triggers defined to fire when a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, or UPDATE STATISTICS statement is executed on the database or server on which it is defined.  
  
 You cannot create memory\-optimized tables if the database or server has one or more DDL trigger defined on CREATE\_TABLE or any event group that includes it. You cannot drop a memory\-optimized table if the database or server has one or more DDL trigger defined on DROP\_TABLE or any event group that includes it.  
  
 You cannot create natively compiled stored procedures if there are one or more DDL triggers on CREATE\_PROCEDURE, DROP\_PROCEDURE, or any event group that includes those events.  
  
## See Also  
 [Migrating to In-Memory OLTP](../../Topics\TopicNameNotContainA/Migrating-to-In-Memory-OLTP.md)  
  
  