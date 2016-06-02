---
title: Replay to a Cursor (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
---
# Replay to a Cursor (SQL Server Profiler)
  This topic describes how to replay trace files or tables that pause when a cursor is reached by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)]. Pausing traces at cursors supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.  
  
### To replay to the cursor  
  
1.  Open the trace file or trace table you want to replay. For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md).  
  
     Make sure that the trace file or table you open contains the event classes necessary for replay. For more information, see [Replay Requirements](../../Topics\TopicNameNotContainA/Replay-Requirements.md).  
  
2.  In the trace window, click an event.  
  
3.  On the **Replay** menu, click **Run to Cursor**, and then connect to the server where you want to replay the trace.  
  
4.  In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.  
  
     The replay starts, pausing when the first cursor is reached.  
  
5.  Press F5 to resume the trace.  
  
6.  Repeat Step 5 through the end of the trace.  
  
## See Also  
 [Replay to a Breakpoint &#40;SQL Server Profiler&#41;](../Topic/Replay%20to%20a%20Breakpoint%20\(SQL%20Server%20Profiler\).md)   
 [Replay Traces](../../Topics\TopicNameNotContainA/Replay-Traces.md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  