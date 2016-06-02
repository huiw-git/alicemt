---
title: Start SQL Server Profiler
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
---
# Start SQL Server Profiler
  You can start [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] in several different ways to support gathering trace output in a variety of scenarios. You can start [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] include from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor, and from several locations in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 When you first start [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] and select **New Trace** from the **File** menu, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance to which you want to connect.  
  
### To start SQL Server Profiler from the Start menu  
  
1.  On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)], point to **Performance Tools**, and then click **SQL Server Profiler**.  
  
### To start SQL Server Profiler in Database Engine Tuning Advisor  
  
1.  On the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor **Tools** menu, click **SQL Server Profiler**.  
  
## Starting SQL Server Profiler in Management Studio  
 [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] starts each profiler session in its own instance and continues to run if you shutdown [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 You can start [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] from several locations in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], as illustrated in the following procedures. When [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] starts it loads the connection context, trace template, and filter context of its launch point.  
  
#### To start SQL Server Profiler from the Tools menu  
  
1.  In the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] **Tools** menu, click **SQL Server Profiler**.  
  
#### To start SQL Server Profiler from the Query Editor  
  
1.  On the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] menu bar, click **New Query**.  
  
2.  In Query Editor, right\-click and then select **Trace Query in SQL Server Profiler**.  
  
    > [!NOTE]  
    >  The connection context is the editor connection, the trace template is TSQL\_SPs, and the applied filter is SPID \= query window SPID.  
  
#### To start SQL Server Profiler from Activity Monitor  
  
1.  In Object Explorer, right\-click an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and then click **Activity Monitor**.  
  
2.  Click the **Processes** pane, right\-click the process that you want to profile, and then click **Trace Process in SQL Server Profiler**.  
  
    > [!NOTE]  
    >  When a process is selected, the connection context is the Object Explorer connection when Activity Monitor was opened. The trace template is the default based on the server type, and the SPID equals the SPID for the selected process.  
  
## .NET Framework Security  
 In Windows Authentication mode, the user account that runs [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] must have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 To perform tracing with [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], users must also have the ALTER TRACE permission.  
  
## See Also  
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)   
 [Use SQL Server Management Studio](../Topic/Use%20SQL%20Server%20Management%20Studio.md)  
  
  