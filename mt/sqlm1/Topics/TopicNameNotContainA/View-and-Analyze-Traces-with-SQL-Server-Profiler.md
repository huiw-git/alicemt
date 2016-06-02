---
title: View and Analyze Traces with SQL Server Profiler
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
---
# View and Analyze Traces with SQL Server Profiler
  Use [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to view captured event data in a trace. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays data based on defined trace properties. One way to analyze [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data is to copy the data to another program, such as [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor. [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor can use a trace file that contains SQL batch and remote procedure call \(RPC\) events if the **Text** data column is included in the trace. To make sure that the correct events and columns are captured for use with [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor, use the predefined Tuning template that is supplied with [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].  
  
 When you open a trace by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], the trace file does not need to have the .trc file extension if the file was created by either [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] or SQL Trace system stored procedures.  
  
> [!NOTE]  
>  [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] can also read SQL Trace .log files and generic SQL script files. When opening a SQL Trace .log file that does not have a .log file extension, such as trace.txt, specify **SQLTrace\_Log** as the file format.  
  
 You can configure the [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] date and time display format to assist in trace analysis.  
  
## Troubleshooting Data  
 Using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], you can troubleshoot data by grouping traces or trace files by the **Duration**, **CPU**, **Reads**, or **Writes** data columns. Examples of data you might troubleshoot are queries that perform poorly or that have exceptionally high numbers of logical read operations.  
  
 Additional information can be found by saving traces to tables and using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to query the event data. For example, to determine which **SQL:BatchCompleted** events had excessive wait time, execute the following:  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  The server reports the duration of an event in microseconds \(10^\-6 seconds\) and the amount of CPU time used by the event in milliseconds \(10^\-3 seconds\). The [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] graphical user interface displays the **Duration** column in milliseconds by default, but when a trace is saved to either a file or a database table, the **Duration** column value is written in microseconds.  
  
## Displaying Object Names When Viewing Traces  
 If you wish to display the name of an object rather than the object identifier \(**Object ID**\), you must capture the **Server Name** and **Database ID** data columns along with the **Object Name** data column.  
  
 If you choose to group by the **Object ID** data column, make sure you group by the **Server Name** and **Database ID** data columns first, and then by the **Object ID** data column. Similarly, if you choose to group by the **Index ID** data column, make sure you group by the **Server Name**, **Database ID**, and **Object ID** data columns first, and then by the **Index ID** data columns. You must group in this order because object and index IDs are not unique among servers and databases \(and among objects for index IDs\).  
  
## Finding Specific Events Within a Trace  
 To find and group events in a trace, follow these steps:  
  
1.  Create your trace.  
  
    -   When defining the trace, capture the **Event Class**, **ClientProcessID**, and **Start Time** data columns in addition to any other data columns you want to capture. For more information, see [Create a Trace &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Trace%20\(SQL%20Server%20Profiler\).md).  
  
    -   Group the captured data by the **Event Class**data column, and capture the trace to a file or table. To group the captured data, click **Organize Columns** on the **Events Selection** tab of the Trace Properties dialog box. For more information, see [Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../Topic/Organize%20Columns%20Displayed%20in%20a%20Trace%20\(SQL%20Server%20Profiler\).md).  
  
    -   Start the trace and stop it after the appropriate time has passed or number of events have been captured.  
  
2.  Find the target events.  
  
    -   Open the trace file or table, and expand the node of the desired event class; for example, **Deadlock Chain**. For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md).  
  
    -   Search through the trace data until you find the events for which you are looking \(use the **Find** command on the **Edit** menu of [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to help you find values in the trace\). Note the values in the **ClientProcessID** and **Start Time** data columns of the events you trace.  
  
3.  Display the events in context.  
  
    -   Display the trace properties, and group by the **ClientProcessID**data column rather than by the **Event Class** data column.  
  
    -   Expand the nodes of each client process ID you want to view. Search through the trace manually, or use **Find** until you find the previously noted **Start Time**values of the target events. The events are displayed in chronological order with the other events that belong to each selected client process ID. For example, the **Deadlock** and **Deadlock Chain**events, captured within the trace, appear immediately after the **SQL:BatchStarting**events within the expanded client process ID.  
  
 The same technique can be used to find any grouped events. Once you have found the events you seek, group them by **ClientProcessID**, **ApplicationName**, or another event class to view related activity in chronological order.  
  
## See Also  
 [View a Saved Trace &#40;Transact-SQL&#41;](../Topic/View%20a%20Saved%20Trace%20\(Transact-SQL\).md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../Topic/sys.fn_trace_getinfo%20\(Transact-SQL\).md)   
 [View Filter Information &#40;SQL Server Profiler&#41;](../Topic/View%20Filter%20Information%20\(SQL%20Server%20Profiler\).md)   
 [View Filter Information &#40;Transact-SQL&#41;](../Topic/View%20Filter%20Information%20\(Transact-SQL\).md)   
 [Open a Trace File &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)   
 [Open a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)  
  
  