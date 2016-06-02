---
title: Server Performance and Activity Monitoring
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
---
# Server Performance and Activity Monitoring
  The goal of monitoring databases is to assess how a server is performing. Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows operating system provide utilities that let you view the current condition of the database and to track performance as conditions change.  
  
 The following section contains topics that describe how to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows performance and activity monitoring tools. It contains the following topics:  
  
## In This Section  
 **To perform monitoring tasks with Windows tools**  
  
-   [Start System Monitor &#40;Windows&#41;](../Topic/Start%20System%20Monitor%20\(Windows\).md)  
  
-   [View the Windows Application Log &#40;Windows&#41;](../Topic/View%20the%20Windows%20Application%20Log%20\(Windows\).md)  
  
 **To create SQL Server database alerts with Windows tools**  
  
-   [Set Up a SQL Server Database Alert &#40;Windows&#41;](../Topic/Set%20Up%20a%20SQL%20Server%20Database%20Alert%20\(Windows\).md)  
  
 **To perform monitoring tasks with SQL Server Management Studio**  
  
-   [View the SQL Server Error Log &#40;SQL Server Management Studio&#41;](../Topic/View%20the%20SQL%20Server%20Error%20Log%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../Topic/Open%20Activity%20Monitor%20\(SQL%20Server%20Management%20Studio\).md)  
  
 **To perform monitoring tasks with SQL Trace by using Transact\-SQL stored procedures**  
  
-   [Create a Trace &#40;Transact-SQL&#41;](../Topic/Create%20a%20Trace%20\(Transact-SQL\).md)  
  
-   [Set a Trace Filter &#40;Transact-SQL&#41;](../Topic/Set%20a%20Trace%20Filter%20\(Transact-SQL\).md)  
  
-   [Modify an Existing Trace &#40;Transact-SQL&#41;](../Topic/Modify%20an%20Existing%20Trace%20\(Transact-SQL\).md)  
  
-   [View a Saved Trace &#40;Transact-SQL&#41;](../Topic/View%20a%20Saved%20Trace%20\(Transact-SQL\).md)  
  
-   [View Filter Information &#40;Transact-SQL&#41;](../Topic/View%20Filter%20Information%20\(Transact-SQL\).md)  
  
-   [Delete a Trace &#40;Transact-SQL&#41;](../Topic/Delete%20a%20Trace%20\(Transact-SQL\).md)  
  
 **To create and modify traces by using SQL Server Profiler**  
  
-   [Create a Trace &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [Set Global Trace Options &#40;SQL Server Profiler&#41;](../Topic/Set%20Global%20Trace%20Options%20\(SQL%20Server%20Profiler\).md)  
  
-   [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../Topic/Specify%20Events%20and%20Data%20Columns%20for%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)  
  
-   [Create a Transact-SQL Script for Running a Trace &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Transact-SQL%20Script%20for%20Running%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [Save Trace Results to a File &#40;SQL Server Profiler&#41;](../Topic/Save%20Trace%20Results%20to%20a%20File%20\(SQL%20Server%20Profiler\).md)  
  
-   [Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;](../Topic/Set%20a%20Maximum%20File%20Size%20for%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)  
  
-   [Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../Topic/Save%20Trace%20Results%20to%20a%20Table%20\(SQL%20Server%20Profiler\).md)  
  
-   [Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Set%20a%20Maximum%20Table%20Size%20for%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)  
  
-   [Filter Events in a Trace &#40;SQL Server Profiler&#41;](../Topic/Filter%20Events%20in%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [View Filter Information &#40;SQL Server Profiler&#41;](../Topic/View%20Filter%20Information%20\(SQL%20Server%20Profiler\).md)  
  
-   [Modify a Filter &#40;SQL Server Profiler&#41;](../Topic/Modify%20a%20Filter%20\(SQL%20Server%20Profiler\).md)  
  
-   [Filter Events Based on the Event Start Time &#40;SQL Server Profiler&#41;](../Topic/Filter%20Events%20Based%20on%20the%20Event%20Start%20Time%20\(SQL%20Server%20Profiler\).md)  
  
-   [Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;](../Topic/Filter%20Events%20Based%20on%20the%20Event%20End%20Time%20\(SQL%20Server%20Profiler\).md)  
  
-   [Filter Server Process IDs &#40;SPIDs&#41; in a Trace &#40;SQL Server Profiler&#41;](../Topic/Filter%20Server%20Process%20IDs%20\(SPIDs\)%20in%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../Topic/Organize%20Columns%20Displayed%20in%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
 **To start, pause, and stop traces by using SQL Server Profiler**  
  
-   [Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../Topic/Start%20a%20Trace%20Automatically%20after%20Connecting%20to%20a%20Server%20\(SQL%20Server%20Profiler\).md)  
  
-   [Pause a Trace &#40;SQL Server Profiler&#41;](../Topic/Pause%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [Stop a Trace &#40;SQL Server Profiler&#41;](../Topic/Stop%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;](../Topic/Run%20a%20Trace%20After%20It%20Has%20Been%20Paused%20or%20Stopped%20\(SQL%20Server%20Profiler\).md)  
  
 **To open traces and configure how traces are displayed by using SQL Server Profiler**  
  
-   [Open a Trace File &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)  
  
-   [Open a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)  
  
-   [Clear a Trace Window &#40;SQL Server Profiler&#41;](../Topic/Clear%20a%20Trace%20Window%20\(SQL%20Server%20Profiler\).md)  
  
-   [Close a Trace Window &#40;SQL Server Profiler&#41;](../Topic/Close%20a%20Trace%20Window%20\(SQL%20Server%20Profiler\).md)  
  
-   [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](../Topic/Set%20Trace%20Definition%20Defaults%20\(SQL%20Server%20Profiler\).md)  
  
-   [Set Trace Display Defaults &#40;SQL Server Profiler&#41;](../Topic/Set%20Trace%20Display%20Defaults%20\(SQL%20Server%20Profiler\).md)  
  
 **To replay traces by using SQL Server Profiler**  
  
-   [Replay a Trace File &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)  
  
-   [Replay a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)  
  
-   [Replay a Single Event at a Time &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Single%20Event%20at%20a%20Time%20\(SQL%20Server%20Profiler\).md)  
  
-   [Replay to a Breakpoint &#40;SQL Server Profiler&#41;](../Topic/Replay%20to%20a%20Breakpoint%20\(SQL%20Server%20Profiler\).md)  
  
-   [Replay to a Cursor &#40;SQL Server Profiler&#41;](../Topic/Replay%20to%20a%20Cursor%20\(SQL%20Server%20Profiler\).md)  
  
-   [Replay a Transact-SQL Script &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Transact-SQL%20Script%20\(SQL%20Server%20Profiler\).md)  
  
 **To create, modify, and use trace templates by using SQL Server Profiler**  
  
-   [Create a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)  
  
-   [Modify a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Modify%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)  
  
-   [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../Topic/Derive%20a%20Template%20from%20a%20Running%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../Topic/Derive%20a%20Template%20from%20a%20Trace%20File%20or%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)  
  
-   [Export a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Export%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)  
  
-   [Import a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Import%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)  
  
 **To use SQL Server Profiler traces to collect and monitor server performance**  
  
-   [Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;](../Topic/Find%20a%20Value%20or%20Data%20Column%20While%20Tracing%20\(SQL%20Server%20Profiler\).md)  
  
-   [Save Deadlock Graphs &#40;SQL Server Profiler&#41;](../Topic/Save%20Deadlock%20Graphs%20\(SQL%20Server%20Profiler\).md)  
  
-   [Save Showplan XML Events Separately &#40;SQL Server Profiler&#41;](../Topic/Save%20Showplan%20XML%20Events%20Separately%20\(SQL%20Server%20Profiler\).md)  
  
-   [Save Showplan XML Statistics Profile Events Separately &#40;SQL Server Profiler&#41;](../Topic/Save%20Showplan%20XML%20Statistics%20Profile%20Events%20Separately%20\(SQL%20Server%20Profiler\).md)  
  
-   [Extract a Script from a Trace &#40;SQL Server Profiler&#41;](../Topic/Extract%20a%20Script%20from%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
-   [Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;](../Topic/Correlate%20a%20Trace%20with%20Windows%20Performance%20Log%20Data%20\(SQL%20Server%20Profiler\).md)  
  
  