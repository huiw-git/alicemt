---
title: Replay a Transact-SQL Script (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
---
# Replay a Transact-SQL Script (SQL Server Profiler)
  When you test possible solutions to a performance problem, use [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to replay [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts, and compare performance before and after your changes.  
  
### To replay a Transact\-SQL script  
  
1.  On the **File** menu, point to **Open**, and then click **Script File**.  
  
2.  Select the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script file you want to open. Make sure that the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script contains events necessary for replay. For more information, see [Replay Requirements](../../Topics\TopicNameNotContainA/Replay-Requirements.md).  
  
3.  On the **Replay** menu, click **Start**, and connect to the server where you want to replay the script.  
  
4.  In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.  
  
## See Also  
 [Replay Traces](../../Topics\TopicNameNotContainA/Replay-Traces.md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  