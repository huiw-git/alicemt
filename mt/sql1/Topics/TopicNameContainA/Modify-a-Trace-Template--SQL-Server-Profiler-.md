---
title: Modify a Trace Template (SQL Server Profiler)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
---
# Modify a Trace Template (SQL Server Profiler)
  This topic describes how to modify a trace template by using [!INCLUDE[ssSqlProfiler](../../Token/Other/ssSqlProfiler_md.md)].  
  
### To modify a trace template  
  
1.  On the **File** menu, point to **Templates**, and then click **Edit Template**.  
  
2.  In the **Trace Template Properties** dialog box, on the **General** tab, you can modify the server type and template name, or choose to use a default template for the server type.  
  
3.  On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows.  
  
    -   To add an event, expand the appropriate event category in the **Events** column, and then select the event name.  
  
    -   When you add an event, all relevant data columns are included by default. To remove a data column for an event from a trace, clear the check box in the data column for the event.  
  
    -   To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box. You can also right\-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box. Click **OK** to add the filter.  
  
4.  Click **Save**, or click **Save As**to save the trace template under another name.  
  
## See Also  
 [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Specify-Events-and-Data-Columns-for-a-Trace-File--SQL-Server-Profiler-.md)   
 [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Derive-a-Template-from-a-Running-Trace--SQL-Server-Profiler-.md)   
 [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Derive-a-Template-from-a-Trace-File-or-Trace-Table--SQL-Server-Profiler-.md)   
 [SQL Server Profiler Templates and Permissions](../../Topics/TopicNameNotContainA/SQL-Server-Profiler-Templates-and-Permissions.md)   
 [SQL Server Profiler](../../Topics/TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  