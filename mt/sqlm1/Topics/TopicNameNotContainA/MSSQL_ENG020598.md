---
title: MSSQL_ENG020598
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
---
# MSSQL_ENG020598
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|20598|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The row was not found at the Subscriber when applying the replicated command.|  
  
## Explanation  
 This error is raised in transactional replication if the Distribution Agent attempts to update a row at the Subscriber, but the row has been deleted or the primary key of the row has been changed. By default, Subscribers to transactional publications should be treated as read\-only, because changes are not propagated back to the Publisher. For transactional replication, user changes should be made at the Subscriber only if updatable subscriptions or peer\-to\-peer replication is used. For information about these options, see [Updatable Subscriptions for Transactional Replication](../../Topics\TopicNameNotContainA/Updatable-Subscriptions-for-Transactional-Replication.md) and [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md).  
  
## User Action  
 **To resolve this problem:**  
  
1.  If replication must continue while you identify the source of the error, specify the parameter **\-SkipErrors 20598** for the Distribution Agent. This allows the agent to skip changes that result in error 20598, while allowing other changes to be replicated.  
  
2.  Identify which rows at the Subscriber have been deleted or have a different primary key than the corresponding rows at the Publisher. You can use the [tablediff Utility](../../Topics\TopicNameNotContainA/tablediff-Utility.md) to determine which rows are different in the publication and subscription databases. For information about using this utility with replicated databases, see [Compare Replicated Tables for Differences &#40;Replication Programming&#41;](../Topic/Compare%20Replicated%20Tables%20for%20Differences%20\(Replication%20Programming\).md).  
  
3.  Correct the rows at the Subscriber using the **tablediff** utility or another method.  
  
4.  \(Optional\) Remove the **\-SkipErrors** parameter.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  