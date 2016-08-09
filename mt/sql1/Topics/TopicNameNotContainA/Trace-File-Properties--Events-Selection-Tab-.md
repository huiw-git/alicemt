---
title: "Trace File Properties (Events Selection Tab)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
caps.latest.revision: 24
manager: jhubbard
---
# Trace File Properties (Events Selection Tab)
Use the **Events Selection** tab of the **Trace File Template Properties** dialog box to view the column properties of the trace or remove data columns from the trace.  
  
 To view this window, open a trace file. Then, on the **File** menu, click **Properties**, and then click the **Events Selection** tab.  
  
## Options  
 **Events** column  
 View traced events which are organized by event category. Initially, all events in the trace are selected. Events can be selected by checking the box or by checking a data column for an event. If the event box is checked, all data columns available for that event are selected. If the data column for an event is checked, the event is checked and any other required column is also automatically checked. If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis. You can also change column filters to reduce the amount of visible data in the trace window. For more information about event classes, see [SQL Server Event Class Reference](../../Topics/TopicNameNotContainA/SQL-Server-Event-Class-Reference.md).  
  
 Data Columns  
 View traced data columns. All relevant data columns in the trace are checked by default for each event included in the trace.  
  
 Specify filters by clicking the data column heading and entering the filter criteria. Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.  
  
 **Show all events**  
 Show all available events. By default, only rows in the **Events Selection** grid that are selected display. Uncheck this box to hide all unselected events in the **Events Selection** grid. If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.  
  
 **Show all columns**  
 Show all available data columns. By default, only data columns that are selected display. Uncheck this box to hide all unselected data columns in the **Events Selection** grid.  
  
 **Column Filters**  
 Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label for filtered data columns. Use the **Edit Filter** dialog box to edit data column filters.  
  
 **Organize Columns**  
 After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.  
  
## See Also  
 [Specify Events and Data Columns for a Trace File (SQL Server Profiler)](../../Topics/TopicNameContainA/Specify-Events-and-Data-Columns-for-a-Trace-File--SQL-Server-Profiler-.md)   
 [Filter Events in a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Filter-Events-in-a-Trace--SQL-Server-Profiler-.md)   
 [View Filter Information (SQL Server Profiler)](../../Topics/TopicNameNotContainA/View-Filter-Information--SQL-Server-Profiler-.md)   
 [Modify a Filter (SQL Server Profiler)](../../Topics/TopicNameContainA/Modify-a-Filter--SQL-Server-Profiler-.md)   
 [SQL Server Profiler](../../Topics/TopicNameNotContainA/SQL-Server-Profiler.md)   
 [SQL Server Profiler Templates and Permissions](../../Topics/TopicNameNotContainA/SQL-Server-Profiler-Templates-and-Permissions.md)