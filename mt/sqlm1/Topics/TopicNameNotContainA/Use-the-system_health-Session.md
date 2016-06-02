---
title: Use the system_health Session
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
---
# Use the system_health Session
  The system\_health session is an Extended Events session that is included by default with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This session starts automatically when the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] starts, and runs without any noticeable performance effects. The session collects system data that you can use to help troubleshoot performance issues in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. Therefore, we recommend that you do not stop or delete the session.  
  
 The session collects information that includes the following:  
  
-   The sql\_text and session\_id for any sessions that encounter an error that has a severity \>\=20.  
  
-   The sql\_text and session\_id for any sessions that encounter a memory\-related error. The errors include 17803, 701, 802, 8645, 8651, 8657 and 8902.  
  
-   A record of any non\-yielding scheduler problems. \(These appear in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log as error 17883.\)  
  
-   Any deadlocks that are detected.  
  
-   The callstack, sql\_text, and session\_id for any sessions that have waited on latches \(or other interesting resources\) for \> 15 seconds.  
  
-   The callstack, sql\_text, and session\_id for any sessions that have waited on locks for \> 30 seconds.  
  
-   The callstack, sql\_text, and session\_id for any sessions that have waited for a long time for preemptive waits. The duration varies by wait type. A preemptive wait is where [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is waiting for external API calls.  
  
-   The callstack and session\_id for CLR allocation and virtual allocation failures.  
  
-   The ring\_buffer events for the memory broker, scheduler monitor, memory node OOM, security, and connectivity.  
  
-   System component results from sp\_server\_diagnostics.  
  
-   Instance health collected by scheduler\_monitor\_system\_health\_ring\_buffer\_recorded.  
  
-   CLR Allocation failures.  
  
-   Connectivity errors using connectivity\_ring\_buffer\_recorded.  
  
-   Security errors using security\_error\_ring\_buffer\_recorded.  
  
## Viewing the Session Data  
 The session uses the ring buffer target to store the data. To view the session data, use the following query:  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
 To view the session data from the event file, use the Extended Events user interface available in Management Studio. See [View Event Session Data](../../Topics\TopicNameNotContainA/View-Event-Session-Data.md) for more information.  
  
## Restoring the system\_health Session  
 If you delete the system\_health session, you can restore it by executing the **u\_tables.sql** file in Query Editor. This file is located in the following folder, where C: represents the drive where you installed the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] program files:  
  
 C:\\Program Files\\Microsoft SQL Server\\MSSQL13.\<*instanceid*\>\\MSSQL\\Install  
  
 Be aware that after you restore the session, you must start the session by using the ALTER EVENT SESSION statement or by using the **Extended Events** node in Object Explorer. Otherwise, the session starts automatically the next time that you restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.  
  
## See Also  
 [Extended Events Tools](../../Topics\TopicNameNotContainA/Extended-Events-Tools.md)  
  
  