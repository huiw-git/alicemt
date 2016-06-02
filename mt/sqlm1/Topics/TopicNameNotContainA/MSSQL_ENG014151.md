---
title: MSSQL_ENG014151
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
---
# MSSQL_ENG014151
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14151|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Replication\-%s: agent %s failed. %s|  
  
## Explanation  
 This error is raised for any replication agent failure. The text at the end of the message depends on the context of the failure.  
  
## User Action  
 This error can occur in a number of situations; use the following approaches as necessary:  
  
-   Restart the failed agent to see if it will now run without failures. For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
-   Check the agent history and job history for other errors that occurred around the same time. For information about viewing agent status and error details in Replication Monitor, see the following topics:  
  
    -   For the Snapshot Agent, Log Reader Agent, and Queue Reader Agent, see [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Publication%20\(Replication%20Monitor\).md).  
  
    -   For the Distribution Agent and Merge Agent, see [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md).  
  
-   Verify that basic connectivity is working between the computers accessed by the agent, and then connect to each computer with a utility like the [sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md). When connecting, use the same account under which the agent makes connections. For more information about the permissions required by each agent account, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
-   If the error occurs while creating or applying a snapshot, check the files in the snapshot directory for errors.  
  
-   If the error continues to occur, increase the logging of the agent and specify an output file for the log. Depending on the context of the error, this could provide the steps leading up to the error and\/or additional error messages.  
  
## See Also  
 [Replication Agent Administration](../../Topics\TopicNameNotContainA/Replication-Agent-Administration.md)   
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)   
 [Replication Distribution Agent](../../Topics\TopicNameNotContainA/Replication-Distribution-Agent.md)   
 [Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md)   
 [Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md)   
 [Replication Queue Reader Agent](../../Topics\TopicNameNotContainA/Replication-Queue-Reader-Agent.md)   
 [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md)  
  
  