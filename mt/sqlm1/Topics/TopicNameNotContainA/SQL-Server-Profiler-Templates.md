---
title: SQL Server Profiler Templates
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b674e491-dc58-47a1-acdd-7028e9a201fc
---
# SQL Server Profiler Templates
  You can use [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to create templates that define the event classes and data columns to include in traces. After you define and save the template, you can run a trace that records the data for each event class you selected. You can use a template on many traces; the template is not itself executed.  
  
 [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] offers predefined trace templates that allow you to easily configure the event classes that you will most likely need for specific traces. The Standard template, for example, helps you to create a generic trace for recording logins, logouts, batches completed, and connection information. You can use this template to run traces without modification or as a starting point for additional templates with different event configurations.  
  
> [!NOTE]  
>  In addition to traces from predefined templates, [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] also allows you to create them from a blank template, containing no event classes by default. Using the blank trace template can be useful when a planned trace does not resemble the configurations of any of the predefined templates.  
  
 [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] can trace a variety of server types. For example you can trace [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  However, the event classes that can be included are not the same for each type of server. Therefore, [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] maintains different templates for different servers, and makes available the specific template that matches the selected server type.  
  
## Predefined Templates  
 In addition to the Standard \(default\) template, [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] includes several predefined templates for monitoring certain types of events. The following table lists the predefined templates, their purpose, and the event classes for which they capture information.  
  
|Template name|Template purpose|Event classes|  
|-------------------|----------------------|-------------------|  
|SP\_Counts|Captures stored procedure execution behavior over time.|**SP:Starting**|  
|Standard|Generic starting point for creating a trace. Captures all stored procedures and [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] batches that are run. Use to monitor general database server activity.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC:Completed**<br /><br /> **SQL:BatchCompleted**<br /><br /> **SQL:BatchStarting**|  
|TSQL|Captures all [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that are submitted to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by clients and the time issued. Use to debug client applications.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC:Starting**<br /><br /> **SQL:BatchStarting**|  
|TSQL\_Duration|Captures all [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements submitted to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by clients, their execution time \(in milliseconds\), and groups them by duration. Use to identify slow queries.|**RPC:Completed**<br /><br /> **SQL:BatchCompleted**|  
|TSQL\_Grouped|Captures all [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements submitted to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and the time they were issued. Groups information by user or client that submitted the statement. Use to investigate queries from a particular client or user.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC:Starting**<br /><br /> **SQL:BatchStarting**|  
|TSQL\_Locks|Captures all of the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that are submitted to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by clients along with exceptional lock events. Use to troubleshoot deadlocks, lock time\-out, and lock escalation events.|**Blocked Process Report**<br /><br /> **SP:StmtCompleted**<br /><br /> **SP:StmtStarting**<br /><br /> **SQL:StmtCompleted**<br /><br /> **SQL:StmtStarting**<br /><br /> **Deadlock Graph**<br /><br /> **Lock:Cancel**<br /><br /> **Lock:Deadlock**<br /><br /> **Lock:Deadlock Chain**<br /><br /> **Lock:Escalation**<br /><br /> **Lock:Timeout \(timeout\>0\)**|  
|TSQL\_Replay|Captures detailed information about [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that is required if the trace will be replayed. Use to perform iterative tuning, such as benchmark testing.|**CursorClose**<br /><br /> **CursorExecute**<br /><br /> **CursorOpen**<br /><br /> **CursorPrepare**<br /><br /> **CursorUnprepare**<br /><br /> **Audit Login**<br /><br /> **Audit Logout**<br /><br /> **Existing Connection**<br /><br /> **RPC Output Parameter**<br /><br /> **RPC:Completed**<br /><br /> **RPC:Starting**<br /><br /> **Exec Prepared SQL**<br /><br /> **Prepare SQL**<br /><br /> **SQL:BatchCompleted**<br /><br /> **SQL:BatchStarting**|  
|TSQL\_SPs|Captures detailed information about all executing stored procedures. Use to analyze the component steps of stored procedures. Add the **SP:Recompile** event if you suspect that procedures are being recompiled.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC:Starting**<br /><br /> **SP:Completed**<br /><br /> **SP:Starting**<br /><br /> **SP:StmtStarting**<br /><br /> **SQL:BatchStarting**|  
|Tuning|Captures information about stored procedures and [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] batch execution. Use to produce trace output that [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor can use as a workload to tune databases.|**RPC:Completed**<br /><br /> **SP:StmtCompleted**<br /><br /> **SQL:BatchCompleted**|  
  
 For information about the event classes, see [SQL Server Event Class Reference](../../Topics\TopicNameNotContainA/SQL-Server-Event-Class-Reference.md).  
  
## Default Template  
 [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] automatically designates the **Standard** template as the default template applied to any new trace. However you can change the default template to any other predefined or user\-defined template. To change the default template, select the **Use as a default template for selected server type** check box when you create or edit a template by using the **General** tab of the **Trace Template Properties** dialog box.  
  
 To navigate to the **Trace Template Properties** dialog box, on the [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] **File** menu, choose **Templates**, and then click **New Template** or **Edit Template**.  
  
> [!NOTE]  
>  The default template is specific for a given server type. Changing the default for one server type does not affect the default template for any other server type. For more information about setting a default template for a specific server, see [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](../Topic/Set%20Trace%20Definition%20Defaults%20\(SQL%20Server%20Profiler\).md).  
  
## See Also  
 [Create a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)   
 [Modify a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Modify%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)   
 [Export a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Export%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)   
 [Import a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Import%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)  
  
  