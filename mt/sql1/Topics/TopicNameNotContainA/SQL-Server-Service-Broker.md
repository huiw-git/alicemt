---
title: "SQL Server Service Broker"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
caps.latest.revision: 22
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Service Broker
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] provides native support for messaging and queuing applications in the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]. This makes it easier for developers to create sophisticated applications that use the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] components to communicate between disparate databases. Developers can use [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] to easily build distributed and reliable applications.  
  
 Application developers who use [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] can distribute data workloads across several databases without programming complex communication and messaging internals. This reduces development and test work because [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] handles the communication paths in the context of a conversation. It also improves performance. For example, front-end databases supporting Web sites can record information and send process intensive tasks to queue in back-end databases. [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] ensures that all tasks are managed in the context of transactions to assure reliability and technical consistency.  
  
## Where is the documentation for Service Broker?  
 The reference documentation for [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] is included in the [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] documentation. This reference documentation includes the following sections:  
  
-   [Data Definition Language (DDL) Statements (Transact-SQL)](assetId:///d8d6f62a-e815-425c-a80e-a63fd34ec275) for CREATE, ALTER, and DROP statements  
  
-   [Service Broker Statements](assetId:///5a898bef-a697-4769-b045-dc9d15858a99)  
  
-   [Service Broker Catalog Views (Transact-SQL)](assetId:///00682b5e-4720-422e-a5ec-4a96f26e1300)  
  
-   [Service Broker Related Dynamic Management Views (Transact-SQL)](assetId:///3253bf60-5ea6-4525-8744-c21070c4df0e)  
  
-   [ssbdiagnose Utility (Service Broker)](../../Topics/TopicNameNotContainA/ssbdiagnose-Utility--Service-Broker-.md)  
  
 See the [previously published documentation](http://go.microsoft.com/fwlink/?LinkId=231312) for [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] concepts and for development and management tasks. This documentation is not reproduced in the [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] documentation due to the small number of changes in [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
## What's new in Service Broker  
 No significant changes are introduced in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  The following changes were introduced in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)].  
  
### Messages can be sent to multiple target services (multicast)  
 The syntax of the [SEND (Transact-SQL)](assetId:///b6e66aeb-1714-4c2b-b7c2-d386d77b0d46) statement has been extended to enable multicast by supporting multiple conversation handles.  
  
### Queues expose the message enqueued time  
 Queues have a new column, **message_enqueue_time**, that shows how long a message has been in the queue.  
  
### Poison message handling can be disabled  
 The [CREATE QUEUE (Transact-SQL)](assetId:///fce80faf-2bdc-475d-8ca1-31438ed41fb0) and [ALTER QUEUE (Transact-SQL)](assetId:///d54aa325-8761-4cd4-8da7-acf33df12296) statements now have the ability to enable or disable poison message handling by adding the clause, `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)`. The catalog view **sys.service_queues** now has the column **is_poison_message_handling_enabled** to indicate whether poison message is enabled or disabled.  
  
### Always On support in Service Broker  
 For more information, see [Service Broker with Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Service-Broker-with-Always-On-Availability-Groups--SQL-Server-.md).