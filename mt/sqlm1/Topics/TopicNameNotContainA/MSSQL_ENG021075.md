---
title: MSSQL_ENG021075
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
---
# MSSQL_ENG021075
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21075|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The initial snapshot for publication '%s' is not yet available.|  
  
## Explanation  
 Error MSSQL\_ENG021075 is raised if the Distribution Agent or Merge Agent is started before the Snapshot Agent has finished generating the snapshot.  
  
## User Action  
 If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent or Merge Agent. For more information, see [Create and Apply the Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Snapshot.md).  
  
 If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them. For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Publication%20\(Replication%20Monitor\).md).  
  
 If the error continues to occur, increase the logging of the agent and specify an output file for the log. Depending on the context of the error, this could provide the steps leading up to the error and\/or additional error messages.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  