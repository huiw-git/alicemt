---
title: "Threads Window"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Threads Window
The **Threads** window displays information about the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] thread that is used by the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor session that is being debugged. You must be in debug mode to display the thread information.  
  
## Task List  
 **To access the Threads window**  
  
-   On the **Debug** menu, click **Windows**, and then click **Threads**.  
  
## Columns  
 **ID**  
 Is a unique identifying number that the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] debugger assigns to the thread. You can find more information about the thread by selecting a row from the sys.dm_os_threads dynamic management view.  
  
 If you are not running in lightweight pooling mode, select the row in which the value in os_thread_id matches the value in the **ID** column. If you are running in lightweight pooling mode, select the row in which the value in fiber_context_address matches the value in the **ID** column.  
  
 **Name**  
 Displays information about the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] session in the format **ComputerName/InstanceName [SPID]**.  
  
 **ComputerName**  
 The name of the computer that is running the instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] that the Query Editor session is connected to.  
  
 **InstanceName**  
 The name of the instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] that the Query Editor session is connected to.  
  
 **[SPID]**  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] session process ID that uniquely identifies this session. You can obtain more information about the session by selecting the row in the sys.sysprocesses view that has the same value in the spid column.  
  
 **Location**  
 Displays the name of the script file that is used in the Query Editor session that is being debugged.  
  
 **Priority**  
 The [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] debugger does not support this feature.  
  
 **Suspend**  
 The [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] debugger does not support this feature.  
  
## See Also  
 [Transact-SQL Debugger](../../Topics/TopicNameNotContainA/Transact-SQL-Debugger.md)   
 [Transact-SQL Debugger Information](../../Topics/TopicNameNotContainA/Transact-SQL-Debugger-Information.md)   
 [sys.dm_os_threads (Transact-SQL)](assetId:///a5052701-edbf-4209-a7cb-afc9e65c41c1)   
 [sys.sysprocesses (Transact-SQL)](assetId:///60a36d36-54b3-4bd6-9cac-702205a21b16)