---
title: Create a Trace Template (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
---
# Create a Trace Template (SQL Server Profiler)
  This topic describes how to create a new trace template by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].  
  
### To create a trace template  
  
1.  On the **File** menu, point to **Templates**, and then click **New Template**.  
  
2.  In the **Trace Template Properties** dialog box, select a server type from the **Select server type**list.  
  
3.  In the **New template name** box, enter a template name.  
  
4.  Optionally, click **Base new template on existing one**, and then select a template from the list.  
  
     All events, data columns, and filters are initially set as specified in the selected template.  
  
5.  Optionally, click **Use as a default template for selected server type**.  
  
6.  On the **Events Selection** tab, add, remove, or modify events, data columns, or filters.  
  
7.  On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows:  
  
    -   To add an event, expand the appropriate event category in the **Events** column, and then select the event name.  
  
    -   When you add an event, all relevant data columns are included by default. To remove a data column for an event from a trace, clear the check box in the data column for the event.  
  
    -   To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box. You can also right\-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box. Click **OK** to add the filter.  
  
8.  Click **Save.**  
  
## See Also  
 [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../Topic/Specify%20Events%20and%20Data%20Columns%20for%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)   
 [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../Topic/Derive%20a%20Template%20from%20a%20Running%20Trace%20\(SQL%20Server%20Profiler\).md)   
 [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../Topic/Derive%20a%20Template%20from%20a%20Trace%20File%20or%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)   
 [SQL Server Profiler Templates and Permissions](../../Topics\TopicNameNotContainA/SQL-Server-Profiler-Templates-and-Permissions.md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  