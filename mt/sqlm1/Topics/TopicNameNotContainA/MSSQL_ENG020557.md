---
title: MSSQL_ENG020557
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
---
# MSSQL_ENG020557
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|20557|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Agent shutdown. For more information, see the SQL Server Agent job history for job '%s'.|  
  
## Explanation  
 A replication agent has shut down without writing a reason to the appropriate history table, or the agent was shut down while in the middle of a process.  
  
## User Action  
  
-   Restart the agent to see whether it will now run without failures. For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
-   Check the agent history and job history for other errors that occurred around the same time. For information about how to view agent status and error details in Replication Monitor, see the following topics:  
  
    -   For the Snapshot Agent, Log Reader Agent, and Queue Reader Agent, see [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Publication%20\(Replication%20Monitor\).md).  
  
    -   For the Distribution Agent and Merge Agent, see [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md).  
  
-   Verify that basic connectivity is working between the computers that are accessed by the agent, and then connect to each computer by using a utility, such as the **sqlcmd** utility. When you connect, use the same account under which the agent makes connections. For more information about the permissions that are required by each agent account, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
-   If the error occurs while you are creating or applying a snapshot, check the files in the snapshot directory for errors.  
  
-   If the error continues to occur, increase the logging of the agent and specify an output file for the log. Depending on the context of the error, this could provide the steps leading up to the error and additional error messages. For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](http://support.microsoft.com/kb/312292).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  