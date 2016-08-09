---
title: "MSSQL_ENG014152"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG014152
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14152|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Replication-%s: agent %s scheduled for retry. %s|  
  
## Explanation  
 The specified replication agent has been scheduled to retry the requested operation. The process continues to retry until it reaches the configured maximum number of retry attempts for the job step.  
  
 A retry typically occurs because of one of the following reasons:  
  
-   The **QueryTimeout** value is exceeded.  
  
-   The **LoginTimeout** value is exceeded.  
  
-   The replication process was chosen as a deadlock victim.  
  
## User Action  
 If the retry message is infrequent, no user action is required.  
  
 Use [sp_help_jobstep](assetId:///4a13b804-45f2-4f82-987f-42d9a57dd6db) to view the current setting for the maximum number of times the **Run agent** step for the specified replication agent will retry. You can use the **@retry_attempts** parameter of the [sp_update_jobstep](assetId:///e158802c-c347-4a5d-bf75-c03e5ae56e6b) stored procedure to adjust the number of times a job step retries.  
  
 If the retry message recurs frequently, troubleshoot the issue based on the message that is causing the retry. Check the agent's history for messages that indicate why the retry had to be scheduled. In some cases you may have to enable more detailed logging for your replication agent. For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](http://support.microsoft.com/kb/312292).  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)