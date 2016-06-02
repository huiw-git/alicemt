---
title: SQL Server Profiler - Source Table/Database Engine Tuning Advisor - Select Workload Table
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
---
# SQL Server Profiler - Source Table/Database Engine Tuning Advisor - Select Workload Table
  Microsoft [!INCLUDE[ssSqlProfiler](../../../Token\Other/ssSqlProfiler_md.md)] and [!INCLUDE[ssDE](../../../Token\Other/ssDE_md.md)] Tuning Advisor use this dialog box to select tables.  
  
 In [!INCLUDE[ssSqlProfiler](../../../Token\Other/ssSqlProfiler_md.md)], use the **Source Table** dialog box to specify a source table for a trace table. This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.  
  
 In [!INCLUDE[ssDE](../../../Token\Other/ssDE_md.md)] Tuning Advisor, use the **Select Workload Table** dialog box to select a database table that contains [!INCLUDE[ssSqlProfiler](../../../Token\Other/ssSqlProfiler_md.md)] trace information to use as a tuning workload, or to preview the table contents before starting tuning analysis.  
  
## Options  
 **SQL Server**  
 Specifies the instance of [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)] currently connected. This field is populated automatically and cannot be updated.  
  
 **Database**  
 Specify the database where the trace table is located.  
  
 **Owner**  
 Specifies the owner of the trace table. This field is populated automatically as **dbo**.  
  
 **Table**  
 Specify the name of the trace table from which the trace should be read.  
  
## See Also  
 [Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../Topic/Save%20Trace%20Results%20to%20a%20Table%20\(SQL%20Server%20Profiler\).md)   
 [SQL Server Profiler Templates and Permissions](../../../Topics\TopicNameNotContainA/SQL-Server-Profiler-Templates-and-Permissions.md)   
 [Database Engine Tuning Advisor](../../../Topics\TopicNameNotContainA/Database-Engine-Tuning-Advisor.md)  
  
  