---
title: Isolate Performance Problems
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
---
# Isolate Performance Problems
  It is often more effective to use several [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or Microsoft Windows tools together to isolate database performance problems than to use one tool at a time. For example, the graphical Execution Plan feature, also called Showplan, helps you quickly recognize deadlocks in a single query. However, you can recognize some other performance problems more easily if you use the monitoring features of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows together.  
  
 [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] can be used to monitor and troubleshoot Transact\-SQL and application\-related problems. System Monitor can be used to monitor hardware and other system\-related problems.  
  
 You can monitor the following areas to troubleshoot problems:  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] stored procedures or batches of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements submitted by user applications.  
  
-   User activity, such as blocking locks or deadlocks.  
  
-   Hardware activity, such as disk usage.  
  
 Problems can include:  
  
-   Application development errors involving incorrectly written [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements.  
  
-   Hardware errors, such as disk\- or network\-related errors.  
  
-   Excessive blocking due to an incorrectly designed database.  
  
## Tools for Common Performance Problems  
 Equally important is careful selection of the performance problem that you want each tool to monitor or tune. The tool and the utility depend on the type of performance problem you want to resolve.  
  
 The following topics describe a variety of monitoring and tuning tools and the problems they uncover.  
  
 [Identify Bottlenecks](../../Topics\TopicNameNotContainA/Identify-Bottlenecks.md)  
  
 [Monitor Memory Usage](../../Topics\TopicNameNotContainA/Monitor-Memory-Usage.md)  
  
  