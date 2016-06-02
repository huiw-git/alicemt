---
title: Replay a Trace Table (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a0ad817-3d8d-4495-889d-c66a7ef9e8bb
---
# Replay a Trace Table (SQL Server Profiler)
  Replay is the ability to open a saved trace and replay it again. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. Replay is useful to troubleshoot an application or process problem. When you identify the problem and implement corrections, run the trace that found the potential problem against the corrected application or process. Then, replay the original trace and compare results.  
  
 In addition to any other event classes you want to monitor, specific event classes must be captured to enable replay. These events are captured by default if you use the **TSQL\_Replay** trace template. For more information, see [Replay Requirements](../../Topics\TopicNameNotContainA/Replay-Requirements.md).  
  
### To replay a trace table  
  
1.  Open a trace table that contains the event classes necessary for replay.  
  
2.  On the **Replay** menu, click **Start**, and connect to the server instance where you want to replay the trace.  
  
3.  In the **Replay Configuration** dialog box, on the **Basic Replay Options** tab, specify **Replay server**. Click **Change** to change the server that is displayed in the **Replay server** box.  
  
4.  Optionally, select one of the following destinations in which to save the replay:  
  
    -   **Save to file,** which specifies a file in which to save the replay.  
  
    -   **Save to table**, which specifies a database table in which to save the replay.  
  
5.  Choose either **Replay the events in the order they were traced**or **Replay events using multiple threads**. The following table explains the difference between these settings.  
  
    |Option|Description|  
    |------------|-----------------|  
    |**Replay events in the order they were traced**|Replays events in the order they were recorded. This option enables debugging.|  
    |**Replay events using multiple threads**|This option uses multiple threads to replay each event regardless of the sequence. This option optimizes performance.|  
  
6.  Select **Display replay results** to view the replay as it occurs.  
  
7.  Optionally, click the **Advanced Replay Options**tab to specify the following options:  
  
    -   To replay all server process IDs \(SPIDs\), select **Replay system SPIDs**.  
  
    -   To limit the replay to processes belonging to a specific SPID, select **Replay one SPID only**. In the **SPID to replay**box, type the SPID.  
  
    -   To replay events that occurred during a specific time period, select **Limit replay by date and time**. Select a date and time for the **Start time**and **End time**to specify the time period to include in the replay.  
  
    -   To control how [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] manages processes during replay, configure **Health Monitor Options**.  
  
## See Also  
 [Permissions Required to Run SQL Server Profiler](../../Topics\TopicNameNotContainA/Permissions-Required-to-Run-SQL-Server-Profiler.md)   
 [Replay Traces](../../Topics\TopicNameNotContainA/Replay-Traces.md)   
 [Open a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  