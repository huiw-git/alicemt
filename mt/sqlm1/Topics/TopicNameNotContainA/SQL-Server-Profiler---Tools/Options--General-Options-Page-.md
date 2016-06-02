---
title: SQL Server Profiler - Tools/Options (General Options Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
---
# SQL Server Profiler - Tools/Options (General Options Page)
  Use the **General Options** dialog box to view or specify the following options.  
  
## Options  
  
### Display Options  
 **Font name**  
 Displays the name of the font used in the trace results grid during traces.  
  
 **Font size**  
 Displays the size of the font used in the trace results grid during traces.  
  
 **Choose Font**  
 Opens a dialog to change the font settings.  
  
 **Use regional settings to display date and time values**  
 Displays date and time values in regional settings configured for your computer. If you do not select this option, the date and time values are displayed in the fixed format used by Microsoft [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)], which includes milliseconds.  
  
> [!NOTE]  
>  Toggling this checkbox changes the time columns display format such as **StartTime** and **EndTime**. However, it does not change the **DateTime** value parameters inside the language events or remote procedure calls \(RPCs\).  
  
 **Show values in Duration column in microseconds**  
 Displays the values in microseconds in the **Duration** data column of traces. By default, the **Duration** column displays values in milliseconds.  
  
### Tracing Options  
 **Start tracing immediately after making connection**  
 Begin a trace using the default template as soon as a connection is made.  
  
 **Update trace definition when provider version changes**  
 Apply the most current trace definition to [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)] when the provider is updated. This item is not checked by default. This forces [!INCLUDE[ssSqlProfiler](../../../Token\Other/ssSqlProfiler_md.md)] to query the server for the trace definition and re\-create, if one exists, the file on disk.  
  
### File Rollover Options  
 **Load all rollover files in sequence without prompting**  
 Load rollover files automatically when a trace file is opened. If more than one file was created while tracing, selecting this option automatically loads all rollover files.  
  
 **Prompt before loading rollover files**  
 Have [!INCLUDE[ssSqlProfiler](../../../Token\Other/ssSqlProfiler_md.md)] prompt you before adding a rollover file when a trace file is opened.  
  
 **Never load subsequent rollover files**  
 [!INCLUDE[ssSqlProfiler](../../../Token\Other/ssSqlProfiler_md.md)] never loads subsequent rollover files when a trace file is opened.  
  
### Replay Options  
 **Default number of replay threads**  
 Specify the number of replay threads to use concurrently. A higher number consumes more resources during replay, but increases replay concurrency.  
  
 **Default health monitor wait interval \(sec\)**  
 Specify the wait interval to replay in seconds. Default is 3600 seconds \(1 hour\). This setting affects the amount of time a thread is allowed to run before being terminated by the health monitor.  
  
 **Default health monitor poll interval \(sec\)**  
 Specify the health monitor poll interval during replay in seconds. Default is 60 seconds. This value allows the user to configure how often the health monitor polls for candidates for termination.  
  
## See Also  
 [Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../Topic/Start%20a%20Trace%20Automatically%20after%20Connecting%20to%20a%20Server%20\(SQL%20Server%20Profiler\).md)   
 [Set Trace Display Defaults &#40;SQL Server Profiler&#41;](../Topic/Set%20Trace%20Display%20Defaults%20\(SQL%20Server%20Profiler\).md)   
 [Replay a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)   
 [Replay a Trace File &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)   
 [Replay Traces](../../../Topics\TopicNameNotContainA/Replay-Traces.md)   
 [Set Global Trace Options &#40;SQL Server Profiler&#41;](../Topic/Set%20Global%20Trace%20Options%20\(SQL%20Server%20Profiler\).md)   
 [SQL Server Profiler Templates and Permissions](../../../Topics\TopicNameNotContainA/SQL-Server-Profiler-Templates-and-Permissions.md)   
 [SQL Server Profiler](../../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  