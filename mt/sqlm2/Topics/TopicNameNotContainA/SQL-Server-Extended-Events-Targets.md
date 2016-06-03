---
title: SQL Server Extended Events Targets
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
---
# SQL Server Extended Events Targets
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events targets are event consumers. Targets can write to a file, store event data in a memory buffer, or aggregate event data. Targets can process data synchronously or asynchronously.  
  
 The Extended Events design ensures that targets are guaranteed to receive events once and only once per session.  
  
 Extended Events provide the following targets that you can use for an Extended Events session:  
  
-   [Event counter](../../Topics\TopicNameNotContainA/Event-Counter-Target.md)  
  
     Counts all specified events that occur during an Extended Events session. Use to obtain information about workload characteristics without adding the overhead of full event collection. This is a synchronous target.  
  
-   [Event file](../../Topics\TopicNameNotContainA/Event-File-Target.md)  
  
     Use to write event session output from complete memory buffers to disk. This is an asynchronous target.  
  
-   [Event pairing](../../Topics\TopicNameNotContainA/Event-Pairing-Target.md)  
  
     Many kinds of events occur in pairs, such as lock acquires and lock releases. Use to determine when a specified paired event does not occur in a matched set. This is an asynchronous target.  
  
-   [Event Tracing for Windows \(ETW\)](../../Topics\TopicNameNotContainA/Event-Tracing-for-Windows-Target.md)  
  
     Use to correlate [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] events with Windows operating system or application event data. This is a synchronous target.  
  
-   [Histogram](../../Topics\TopicNameNotContainA/Histogram-Target.md)  
  
     Use to count the number of times that a specified event occurs, based on a specified event column or action. This is an asynchronous target.  
  
-   [Ring buffer](../../Topics\TopicNameNotContainA/Ring-Buffer-Target.md)  
  
     Use to hold the event data in memory on a first\-in first\-out \(FIFO\) basis, or on a per\-event FIFO basis. This is an asynchronous target.  
  
## See Also  
 [Extended Events](../../Topics\TopicNameNotContainA/Extended-Events.md)   
 [SQL Server Extended Events Packages](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Packages.md)   
 [SQL Server Extended Events Sessions](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Sessions.md)   
 [SQL Server Extended Events Engine](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Engine.md)  
  
  