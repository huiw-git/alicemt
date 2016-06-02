---
title: Live Query Statistics
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
---
# Live Query Statistics
  [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] provides the ability to view the live execution plan of an active query. This live query plan provides real\-time insights into the query execution process as the controls flow from one query plan operator to another. The live query plan displays the overall query progress and operator\-level run\-time execution statistics such as the number of rows produced, elapsed time, operator progress, etc. Because this data is available in real time without needing to wait for the query to complete, these execution statistics are extremely useful for debugging query performance issues. \(This feature is available beginning with [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)][!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], however it can work with [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)].\)  
  
||  
|-|  
|**Applies to**: [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \([!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] through [current version](http://go.microsoft.com/fwlink/p/?LinkId=299658)\).|  
  
> [!WARNING]  
>  This feature is primarily intended for troubleshooting purposes. Using this feature can moderately slow the overall query performance. This feature can be used with the [Transact\-SQL Debugger](../../Topics\TopicNameNotContainA/Configure-firewall-rules-before-running-the-TSQL-Debugger.md).  
  
#### To view live query statistics  
  
1.  To view the live query execution plan, on the tools menu click the **Live Query Statistics** icon.  
  
     ![Live Query Stats button on toolbar](../../Images\Image\ImageNotContaina/LiveQueryStatsToolBar.png "LiveQueryStatsToolBar")  
  
     You can also view access the live query execution plan by right clicking on a selected query in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] and then click **Include Live Query Statics**.  
  
     ![Live Query Stats button on popup menu](../../Images\Image\ImageNotContaina/LiveQueryStatsMenu.png "LiveQueryStatsMenu")  
  
2.  Now execute the query. The live query plan displays the overall query progress and the run\-time execution statistics \(e.g. elapsed time, progress, etc.\) for the query plan operators. The query progress information and execution statistics are periodically updated while query execution is in progress. Use this information to understand the overall query execution process and to debug long running queries, queries that run indefinitely, queries that cause tempdb overflow, and timeout issues.  
  
     ![Live Query Stats button in showplan](../../Images\Image\ImageNotContaina/LiveQueryStatsPlan.png "LiveQueryStatsPlan")  
  
 The live execution plan can also be accessed from the **Activity Monitor** by right\-clicking on the queries in the **Active Expensive Queries** table.  
  
 ![Live Query Stats button in Activity Monitor](../../Images\Image\ImageNotContaina/LiveQueryStatsActMon.png "LiveQueryStatsActMon")  
  
## Remarks  
 The statistics profile infrastructure must be enabled before live query statistics can capture information about the progress of queries. Specifying **Include Live Query Statistics** in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] enables the statistics infrastructure for the current query session. There are two other ways to enable the statistics infrastructure which can be used to view the live query statistics from other sessions \(such as from Activity Monitor\).  
  
-   Execute `SET STATISTICS XML ON;` or `SET STATISTICS PROFILE ON;` in the target session.  
  
 or  
  
-   Enable the **query\_post\_execution\_showplan** extended event. This is a server wide setting that enable live query statistics on all sessions. To enable extended events, see [Monitor System Activity Using Extended Events](../../Topics\TopicNameNotContainA/Monitor-System-Activity-Using-Extended-Events.md).  
  
 **Limitations**  
  
-   Natively compiled stored procedures are not supported.  
  
## Permissions  
 Requires the database level **SHOWPLAN** permission to populate the **Live Query Statistics** results page, the server level **VIEW SERVER STATE** permission to see the live statistics, and requires any permissions necessary to execute the query.  
  
## See Also  
 [Monitor and Tune for Performance](../../Topics\TopicNameNotContainA/Monitor-and-Tune-for-Performance.md)   
 [Performance Monitoring and Tuning Tools](../../Topics\TopicNameNotContainA/Performance-Monitoring-and-Tuning-Tools.md)   
 [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../Topic/Open%20Activity%20Monitor%20\(SQL%20Server%20Management%20Studio\).md)   
 [Activity Monitor](../../Topics\TopicNameNotContainA/Activity-Monitor.md)   
 [Monitoring Performance By Using the Query Store](../../Topics\TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md)  
  
  