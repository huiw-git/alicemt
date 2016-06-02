---
title: Replay a Single Event at a Time (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
---
# Replay a Single Event at a Time (SQL Server Profiler)
  This topic describes how to replay one event at a time in a replay trace file or table by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].  
  
### To replay a single event at a time  
  
1.  Open the trace file or trace table you want to replay. For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md).  
  
     Make sure that the trace file or table you open contains the event classes necessary for replay. For more information, see [Replay Requirements](../../Topics\TopicNameNotContainA/Replay-Requirements.md).  
  
2.  On the **Replay** menu, click **Step**, and connect to the server instance where you want to replay the trace.  
  
3.  In the **Replay Configuration** dialog box, verify the settings, and then click **OK**. For more information about specifying settings on the **Replay Configuration** dialog box, see [Replay a Trace File &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md) or [Replay a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md).  
  
4.  To replay the first event, click **OK** in the **Replay Configuration** dialog box.  
  
5.  To replay subsequent events, on the **Replay** menu, click **Step**, or press F10. Repeat clicking **Step** or pressing F10 for each event.  
  
## See Also  
 [Replay Traces](../../Topics\TopicNameNotContainA/Replay-Traces.md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  