---
title: "MSSQL_ENG018752"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG018752
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|18752|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time. If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.|  
  
## Explanation  
 More than one current connection is trying to execute any of the following: **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**. The stored procedures [sp_repldone (Transact-SQL)](assetId:///045d3cd1-712b-44b7-a56a-c9438d4077b9) and [sp_replcmds (Transact-SQL)](assetId:///7e932f80-cc6e-4109-8db4-2b7c8828df73) are stored procedures used by the Log Reader Agent to locate and update information about replicated transactions in a published database. The stored procedure [sp_replshowcmds (Transact-SQL)](assetId:///199f5a74-e08e-4d02-a33c-b8ab0db20f44) is used to troubleshoot certain types of issues with transactional replication.  
  
 This error is raised in the following circumstances:  
  
-   If the Log Reader Agent for a published database is running and a second Log Reader Agent attempts to run against the same database, the error is raised for the second agent and appears in the agent history.  
  
     In a situation where it appears there are multiple agents, it is possible that one of them is the result of an orphaned process.  
  
-   If the Log Reader Agent for a published database is started and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** against the same database, the error is raised in the application where the stored procedure was executed (such as **sqlcmd**).  
  
-   If no Log Reader Agent is running for a published database and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** and then does not close the connection over which the procedure was executed, the error is raised when the Log Reader Agent attempts to connect to the database.  
  
## User Action  
 The following steps can help you to troubleshoot the problem. If any step allows the Log Reader Agent to start without errors, there is no need to complete the remaining steps.  
  
-   Check the history of the Log Reader agent for any other errors that could be contributing to this error. For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks for the Agents Associated With a Publication (Replication Monitor)](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-the-Agents-Associated-With-a-Publication--Replication-Monitor-.md).  
  
-   Check the output of [sp_who (Transact-SQL)](assetId:///132dfb08-fa79-422e-97d4-b2c4579c6ac5) for specific process identification numbers (SPIDs) that are connected to the published database. Close any connections that might have run **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.  
  
-   Restart the Log Reader Agent. For more information, see [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md).  
  
-   Restart the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent service (bring it offline or online in a cluster) on the Distributor. If there is possibility that a scheduled job could have executed **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** from any other [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance, restart the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent for those instances as well. For more information, see [Starting, Stopping, and Pausing SQL Server Agent Service](assetId:///c95a9759-dd30-4ab6-9ab0-087bb3bfb97c).  
  
-   Execute [sp_replflush (Transact-SQL)](assetId:///20809f5f-941d-427f-8f0c-de7a6c487584) at the Publisher on the publication database, and then restart the Log Reader Agent.  
  
-   If the error continues to occur, increase the logging of the agent and specify an output file for the log. Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)   
 [Replication Log Reader Agent](../../Topics/TopicNameNotContainA/Replication-Log-Reader-Agent.md)