---
title: "Replay a Transact-SQL Script (SQL Server Profiler)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# Replay a Transact-SQL Script (SQL Server Profiler)
When you test possible solutions to a performance problem, use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] to replay [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] scripts, and compare performance before and after your changes.  
  
### To replay a Transact-SQL script  
  
1.  On the **File** menu, point to **Open**, and then click **Script File**.  
  
2.  Select the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script file you want to open. Make sure that the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script contains events necessary for replay. For more information, see [Replay Requirements](../../Topics/TopicNameNotContainA/Replay-Requirements.md).  
  
3.  On the **Replay** menu, click **Start**, and connect to the server where you want to replay the script.  
  
4.  In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.  
  
## See Also  
 [Replay Traces](../../Topics/TopicNameNotContainA/Replay-Traces.md)   
 [SQL Server Profiler](../../Topics/TopicNameNotContainA/SQL-Server-Profiler.md)