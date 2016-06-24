---
title: MSSQL_ENG021076
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
---
# MSSQL_ENG021076
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21076|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/includes/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The initial snapshot for article '%s' is not yet available.|  
  
## Explanation  
 Error MSSQL_ENG021076 can be raised if the Distribution Agent is started before the Snapshot Agent has finished generating the snapshot. This error is raised only if the publication contains a single article. If the publication contains more than one article, MSSQL_ENG021075 is raised instead. For more information, see [MSSQL_ENG021075](../../Topics/TopicNameNotContainA/MSSQL_ENG021075.md).  
  
## User Action  
 If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent. For more information, see [Create and Apply the Snapshot](../../Topics/TopicNameNotContainA/Create-and-Apply-the-Snapshot.md).  
  
 If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them. For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-the-Agents-Associated-With-a-Publication--Replication-Monitor-.md).  
  
 If the error continues to occur, increase the logging of the agent and specify an output file for the log. Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)  
  
  