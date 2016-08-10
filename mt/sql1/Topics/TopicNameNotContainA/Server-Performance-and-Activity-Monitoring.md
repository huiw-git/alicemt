---
title: "Server Performance and Activity Monitoring"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
caps.latest.revision: 18
caps.handback.revision: 0
manager: jhubbard
---
# Server Performance and Activity Monitoring
The goal of monitoring databases is to assess how a server is performing. Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends. [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows operating system provide utilities that let you view the current condition of the database and to track performance as conditions change.  
  
 The following section contains topics that describe how to use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and Windows performance and activity monitoring tools. It contains the following topics:  
  
## In This Section  
 **To perform monitoring tasks with Windows tools**  
  
-   [Start System Monitor (Windows)](../../Topics/TopicNameNotContainA/Start-System-Monitor--Windows-.md)  
  
-   [View the Windows Application Log (Windows)](../../Topics/TopicNameNotContainA/View-the-Windows-Application-Log--Windows-.md)  
  
 **To create SQL Server database alerts with Windows tools**  
  
-   [Set Up a SQL Server Database Alert (Windows)](../../Topics/TopicNameContainA/Set-Up-a-SQL-Server-Database-Alert--Windows-.md)  
  
 **To perform monitoring tasks with SQL Server Management Studio**  
  
-   [View the SQL Server Error Log (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-the-SQL-Server-Error-Log--SQL-Server-Management-Studio-.md)  
  
-   [Open Activity Monitor (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Open-Activity-Monitor--SQL-Server-Management-Studio-.md)  
  
 **To perform monitoring tasks with SQL Trace by using Transact-SQL stored procedures**  
  
-   [Create a Trace (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Trace--Transact-SQL-.md)  
  
-   [Set a Trace Filter (Transact-SQL)](../../Topics/TopicNameContainA/Set-a-Trace-Filter--Transact-SQL-.md)  
  
-   [Modify an Existing Trace (Transact-SQL)](../../Topics/TopicNameNotContainA/Modify-an-Existing-Trace--Transact-SQL-.md)  
  
-   [View a Saved Trace (Transact-SQL)](../../Topics/TopicNameContainA/View-a-Saved-Trace--Transact-SQL-.md)  
  
-   [View Filter Information (Transact-SQL)](../../Topics/TopicNameNotContainA/View-Filter-Information--Transact-SQL-.md)  
  
-   [Delete a Trace (Transact-SQL)](../../Topics/TopicNameContainA/Delete-a-Trace--Transact-SQL-.md)  
  
 **To create and modify traces by using SQL Server Profiler**  
  
-   [Create a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Create-a-Trace--SQL-Server-Profiler-.md)  
  
-   [Set Global Trace Options (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Set-Global-Trace-Options--SQL-Server-Profiler-.md)  
  
-   [Specify Events and Data Columns for a Trace File (SQL Server Profiler)](../../Topics/TopicNameContainA/Specify-Events-and-Data-Columns-for-a-Trace-File--SQL-Server-Profiler-.md)  
  
-   [Create a Transact-SQL Script for Running a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Create-a-Transact-SQL-Script-for-Running-a-Trace--SQL-Server-Profiler-.md)  
  
-   [Save Trace Results to a File (SQL Server Profiler)](../../Topics/TopicNameContainA/Save-Trace-Results-to-a-File--SQL-Server-Profiler-.md)  
  
-   [Set a Maximum File Size for a Trace File (SQL Server Profiler)](../../Topics/TopicNameContainA/Set-a-Maximum-File-Size-for-a-Trace-File--SQL-Server-Profiler-.md)  
  
-   [Save Trace Results to a Table (SQL Server Profiler)](../../Topics/TopicNameContainA/Save-Trace-Results-to-a-Table--SQL-Server-Profiler-.md)  
  
-   [Set a Maximum Table Size for a Trace Table (SQL Server Profiler)](../../Topics/TopicNameContainA/Set-a-Maximum-Table-Size-for-a-Trace-Table--SQL-Server-Profiler-.md)  
  
-   [Filter Events in a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Filter-Events-in-a-Trace--SQL-Server-Profiler-.md)  
  
-   [View Filter Information (SQL Server Profiler)](../../Topics/TopicNameNotContainA/View-Filter-Information--SQL-Server-Profiler-.md)  
  
-   [Modify a Filter (SQL Server Profiler)](../../Topics/TopicNameContainA/Modify-a-Filter--SQL-Server-Profiler-.md)  
  
-   [Filter Events Based on the Event Start Time (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Filter-Events-Based-on-the-Event-Start-Time--SQL-Server-Profiler-.md)  
  
-   [Filter Events Based on the Event End Time (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Filter-Events-Based-on-the-Event-End-Time--SQL-Server-Profiler-.md)  
  
-   [Filter Server Process IDs (SPIDs) in a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Filter-Server-Process-IDs--SPIDs--in-a-Trace--SQL-Server-Profiler-.md)  
  
-   [Organize Columns Displayed in a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Organize-Columns-Displayed-in-a-Trace--SQL-Server-Profiler-.md)  
  
 **To start, pause, and stop traces by using SQL Server Profiler**  
  
-   [Start a Trace Automatically after Connecting to a Server (SQL Server Profiler)](../../Topics/TopicNameContainA/Start-a-Trace-Automatically-after-Connecting-to-a-Server--SQL-Server-Profiler-.md)  
  
-   [Pause a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Pause-a-Trace--SQL-Server-Profiler-.md)  
  
-   [Stop a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Stop-a-Trace--SQL-Server-Profiler-.md)  
  
-   [Run a Trace After It Has Been Paused or Stopped (SQL Server Profiler)](../../Topics/TopicNameContainA/Run-a-Trace-After-It-Has-Been-Paused-or-Stopped--SQL-Server-Profiler-.md)  
  
 **To open traces and configure how traces are displayed by using SQL Server Profiler**  
  
-   [Open a Trace File (SQL Server Profiler)](../../Topics/TopicNameContainA/Open-a-Trace-File--SQL-Server-Profiler-.md)  
  
-   [Open a Trace Table (SQL Server Profiler)](../../Topics/TopicNameContainA/Open-a-Trace-Table--SQL-Server-Profiler-.md)  
  
-   [Clear a Trace Window (SQL Server Profiler)](../../Topics/TopicNameContainA/Clear-a-Trace-Window--SQL-Server-Profiler-.md)  
  
-   [Close a Trace Window (SQL Server Profiler)](../../Topics/TopicNameContainA/Close-a-Trace-Window--SQL-Server-Profiler-.md)  
  
-   [Set Trace Definition Defaults (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Set-Trace-Definition-Defaults--SQL-Server-Profiler-.md)  
  
-   [Set Trace Display Defaults (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Set-Trace-Display-Defaults--SQL-Server-Profiler-.md)  
  
 **To replay traces by using SQL Server Profiler**  
  
-   [Replay a Trace File (SQL Server Profiler)](../../Topics/TopicNameContainA/Replay-a-Trace-File--SQL-Server-Profiler-.md)  
  
-   [Replay a Trace Table (SQL Server Profiler)](../../Topics/TopicNameContainA/Replay-a-Trace-Table--SQL-Server-Profiler-.md)  
  
-   [Replay a Single Event at a Time (SQL Server Profiler)](../../Topics/TopicNameContainA/Replay-a-Single-Event-at-a-Time--SQL-Server-Profiler-.md)  
  
-   [Replay to a Breakpoint (SQL Server Profiler)](../../Topics/TopicNameContainA/Replay-to-a-Breakpoint--SQL-Server-Profiler-.md)  
  
-   [Replay to a Cursor (SQL Server Profiler)](../../Topics/TopicNameContainA/Replay-to-a-Cursor--SQL-Server-Profiler-.md)  
  
-   [Replay a Transact-SQL Script (SQL Server Profiler)](../../Topics/TopicNameContainA/Replay-a-Transact-SQL-Script--SQL-Server-Profiler-.md)  
  
 **To create, modify, and use trace templates by using SQL Server Profiler**  
  
-   [Create a Trace Template (SQL Server Profiler)](../../Topics/TopicNameContainA/Create-a-Trace-Template--SQL-Server-Profiler-.md)  
  
-   [Modify a Trace Template (SQL Server Profiler)](../../Topics/TopicNameContainA/Modify-a-Trace-Template--SQL-Server-Profiler-.md)  
  
-   [Derive a Template from a Running Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Derive-a-Template-from-a-Running-Trace--SQL-Server-Profiler-.md)  
  
-   [Derive a Template from a Trace File or Trace Table (SQL Server Profiler)](../../Topics/TopicNameContainA/Derive-a-Template-from-a-Trace-File-or-Trace-Table--SQL-Server-Profiler-.md)  
  
-   [Export a Trace Template (SQL Server Profiler)](../../Topics/TopicNameContainA/Export-a-Trace-Template--SQL-Server-Profiler-.md)  
  
-   [Import a Trace Template (SQL Server Profiler)](../../Topics/TopicNameContainA/Import-a-Trace-Template--SQL-Server-Profiler-.md)  
  
 **To use SQL Server Profiler traces to collect and monitor server performance**  
  
-   [Find a Value or Data Column While Tracing (SQL Server Profiler)](../../Topics/TopicNameContainA/Find-a-Value-or-Data-Column-While-Tracing--SQL-Server-Profiler-.md)  
  
-   [Save Deadlock Graphs (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Save-Deadlock-Graphs--SQL-Server-Profiler-.md)  
  
-   [Save Showplan XML Events Separately (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Save-Showplan-XML-Events-Separately--SQL-Server-Profiler-.md)  
  
-   [Save Showplan XML Statistics Profile Events Separately (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Save-Showplan-XML-Statistics-Profile-Events-Separately--SQL-Server-Profiler-.md)  
  
-   [Extract a Script from a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Extract-a-Script-from-a-Trace--SQL-Server-Profiler-.md)  
  
-   [Correlate a Trace with Windows Performance Log Data (SQL Server Profiler)](../../Topics/TopicNameContainA/Correlate-a-Trace-with-Windows-Performance-Log-Data--SQL-Server-Profiler-.md)