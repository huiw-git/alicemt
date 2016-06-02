---
title: MSSQL_ENG014152
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
---
# MSSQL_ENG014152
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14152|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Replication\-%s: agent %s scheduled for retry. %s|  
  
## Explanation  
 The specified replication agent has been scheduled to retry the requested operation. The process continues to retry until it reaches the configured maximum number of retry attempts for the job step.  
  
 A retry typically occurs because of one of the following reasons:  
  
-   The **QueryTimeout** value is exceeded.  
  
-   The **LoginTimeout** value is exceeded.  
  
-   The replication process was chosen as a deadlock victim.  
  
## User Action  
 If the retry message is infrequent, no user action is required.  
  
 Use [sp\_help\_jobstep](../Topic/sp_help_jobstep%20\(Transact-SQL\).md) to view the current setting for the maximum number of times the **Run agent** step for the specified replication agent will retry. You can use the **@retry\_attempts** parameter of the [sp\_update\_jobstep](../Topic/sp_update_jobstep%20\(Transact-SQL\).md) stored procedure to adjust the number of times a job step retries.  
  
 If the retry message recurs frequently, troubleshoot the issue based on the message that is causing the retry. Check the agent's history for messages that indicate why the retry had to be scheduled. In some cases you may have to enable more detailed logging for your replication agent. For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](http://support.microsoft.com/kb/312292).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  