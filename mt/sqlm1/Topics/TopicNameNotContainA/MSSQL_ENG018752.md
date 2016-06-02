---
title: MSSQL_ENG018752
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
---
# MSSQL_ENG018752
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|18752|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Only one Log Reader Agent or log\-related procedure \(sp\_repldone, sp\_replcmds, and sp\_replshowcmds\) can connect to a database at a time. If you executed a log\-related procedure, drop the connection over which the procedure was executed or execute sp\_replflush over that connection before starting the Log Reader Agent or executing another log\-related procedure.|  
  
## Explanation  
 More than one current connection is trying to execute any of the following: **sp\_repldone**, **sp\_replcmds**, or **sp\_replshowcmds**. The stored procedures [sp_repldone &#40;Transact-SQL&#41;](../Topic/sp_repldone%20\(Transact-SQL\).md) and [sp_replcmds &#40;Transact-SQL&#41;](../Topic/sp_replcmds%20\(Transact-SQL\).md) are stored procedures used by the Log Reader Agent to locate and update information about replicated transactions in a published database. The stored procedure [sp_replshowcmds &#40;Transact-SQL&#41;](../Topic/sp_replshowcmds%20\(Transact-SQL\).md) is used to troubleshoot certain types of issues with transactional replication.  
  
 This error is raised in the following circumstances:  
  
-   If the Log Reader Agent for a published database is running and a second Log Reader Agent attempts to run against the same database, the error is raised for the second agent and appears in the agent history.  
  
     In a situation where it appears there are multiple agents, it is possible that one of them is the result of an orphaned process.  
  
-   If the Log Reader Agent for a published database is started and a user executes **sp\_repldone**, **sp\_replcmds**, or **sp\_replshowcmds** against the same database, the error is raised in the application where the stored procedure was executed \(such as **sqlcmd**\).  
  
-   If no Log Reader Agent is running for a published database and a user executes **sp\_repldone**, **sp\_replcmds**, or **sp\_replshowcmds** and then does not close the connection over which the procedure was executed, the error is raised when the Log Reader Agent attempts to connect to the database.  
  
## User Action  
 The following steps can help you to troubleshoot the problem. If any step allows the Log Reader Agent to start without errors, there is no need to complete the remaining steps.  
  
-   Check the history of the Log Reader agent for any other errors that could be contributing to this error. For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Publication%20\(Replication%20Monitor\).md).  
  
-   Check the output of [sp_who &#40;Transact-SQL&#41;](../Topic/sp_who%20\(Transact-SQL\).md) for specific process identification numbers \(SPIDs\) that are connected to the published database. Close any connections that might have run **sp\_repldone**, **sp\_replcmds**, or **sp\_replshowcmds**.  
  
-   Restart the Log Reader Agent. For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md).  
  
-   Restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service \(bring it offline or online in a cluster\) on the Distributor. If there is possibility that a scheduled job could have executed **sp\_repldone**, **sp\_replcmds**, or **sp\_replshowcmds** from any other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance, restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent for those instances as well. For more information, see [Start, Stop, or Pause the SQL Server Agent Service](../Topic/Start,%20Stop,%20or%20Pause%20the%20SQL%20Server%20Agent%20Service.md).  
  
-   Execute [sp_replflush &#40;Transact-SQL&#41;](../Topic/sp_replflush%20\(Transact-SQL\).md) at the Publisher on the publication database, and then restart the Log Reader Agent.  
  
-   If the error continues to occur, increase the logging of the agent and specify an output file for the log. Depending on the context of the error, this could provide the steps leading up to the error and\/or additional error messages.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)   
 [Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md)  
  
  