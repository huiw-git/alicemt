---
title: Performance Tuning for Oracle Publishers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
---
# Performance Tuning for Oracle Publishers
  The Oracle publishing architecture is similar to the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] publishing architecture; therefore the first step in tuning Oracle replication for performance requires following the general tuning recommendations found in [Enhance General Replication Performance](../../Topics\TopicNameNotContainA/Enhance-General-Replication-Performance.md).  
  
 In addition there are two options for Oracle Publishers that are performance related:  
  
-   Specifying the appropriate publishing option: Oracle or Oracle Gateway.  
  
-   Configuring the transaction set job to process changes on the Publisher at an appropriate interval.  
  
## Specifying the Appropriate Publishing Option  
 The Oracle Gateway option provides improved performance over the Oracle Complete option; however, this option cannot be used to publish the same table in multiple transactional publications. A table can appear in at most one transactional publication and any number of snapshot publications. If you need to publish the same table in multiple transactional publications, choose the Oracle Complete option. Specify this option when identifying the Oracle Publisher at the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor. For more information, see [Create a Publication from an Oracle Database](../../Topics\TopicNameContainA/Create-a-Publication-from-an-Oracle-Database.md).  
  
## Configuring the Transaction Set Job  
 Changes to published Oracle tables are processed in groups called transaction sets. To ensure transactional consistency, each transaction set is committed as a single transaction at the distribution database. If the transaction set becomes too large, it cannot be processed efficiently as a single transaction.  
  
 By default, transaction sets are created only by the Log Reader Agent. If, during periods of high change activity, the Log Reader Agent does not run or cannot connect from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor to the Oracle Publisher, transaction sets can become unmanageably large. To prevent this problem, ensure that transaction sets are created at regular intervals, even if the Log Reader Agent does not run or cannot connect to the Oracle Publisher.  
  
 Transaction sets can be created with the Xactset job \(an Oracle database job installed by replication\), which uses the same mechanism that the Log Reader Agent does to create sets. Each time the job runs, a new transaction set is created. The next time that the Log Reader Agent runs, the agent processes any sets that have been created. If there are still pending changes after all existing transaction sets have been processed, the Log Reader Agent creates and processes one or more additional transaction sets.  
  
 To configure the transaction set job, see [Configure the Transaction Set Job for an Oracle Publisher &#40;Replication Transact-SQL Programming&#41;](../Topic/Configure%20the%20Transaction%20Set%20Job%20for%20an%20Oracle%20Publisher%20\(Replication%20Transact-SQL%20Programming\).md).  
  
## See Also  
 [Configure an Oracle Publisher](../../Topics\TopicNameNotContainA/Configure-an-Oracle-Publisher.md)   
 [Oracle Publishing Overview](../../Topics\TopicNameNotContainA/Oracle-Publishing-Overview.md)  
  
  