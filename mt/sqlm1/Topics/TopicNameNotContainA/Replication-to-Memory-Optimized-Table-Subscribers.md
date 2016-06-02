---
title: Replication to Memory-Optimized Table Subscribers
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
---
# Replication to Memory-Optimized Table Subscribers
  Tables acting as snapshot and transactional replication subscribers, excluding Peer\-to\-peer transactional replication, can be configured as memory\-optimized tables. Other replication configurations are not compatible with memory\-optimized tables. This feature is available beginning with [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
  
## Two configurations are required  
  
-   **Configure the subscriber database to support replication to memory\-optimized tables**  
  
     Set the **@memory\_optimized** property  to **true**, by using [sp_addsubscription &#40;Transact-SQL&#41;](../Topic/sp_addsubscription%20\(Transact-SQL\).md) or [sp_changesubscription &#40;Transact-SQL&#41;](../Topic/sp_changesubscription%20\(Transact-SQL\).md).  
  
-   **Configure the article to support replication to memory\-optimized tables**  
  
     Set the `@schema_option = 0x40000000000` option for the article by using [sp_addarticle &#40;Transact-SQL&#41;](../Topic/sp_addarticle%20\(Transact-SQL\).md) or [sp_changearticle &#40;Transact-SQL&#41;](../Topic/sp_changearticle%20\(Transact-SQL\).md).  
  
#### To configure a memory\-optimized table as a subscriber  
  
1.  Create a transactional publication. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
2.  Add articles to the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
     If configuring by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] set the **@schema\_option** parameter of the **sp\_addarticle** stored procedure to   
    **0x40000000000**.  
  
3.  In the article properties window set **Enable Memory optimization** to **true**.  
  
4.  Start the Snapshot Agent job to generate the initial snapshot for this publication. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
5.  Now create a new subscription. In the **New Subscription Wizard** set **Memory Optimized Subscription** to **true**.  
  
 Memory\-optimized tables should now start receiving updates from the publisher.  
  
#### Reconfigure an existing transaction replication  
  
1.  Go to subscription properties in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] and set **Memory Optimized Subscription** to **true**. The changes are not applied until the subscription is reinitialized.  
  
     If configuring by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] set the new **@memory\_optimized** parameter of the **sp\_addsubscription** stored procedure to true.  
  
2.  Go to the article properties  for a publication in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] and set **Enable Memory** optimization to true.  
  
     If configuring by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] set the **@schema\_option** parameter of the **sp\_addarticle** stored procedure to   
    **0x40000000000**.  
  
3.  Memory optimized tables do not support clustered indexes. To have replication handle this by converting it to nonclustered index on the destination, set **Convert clustered index to nonclustered for memory optimized article** to true.  
  
     If configuring by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] set the **@schema\_option** parameter of the **sp\_addarticle** stored procedure to	**0x0000080000000000**.  
  
4.  Regenerate the snapshot.  
  
5.  Reinitialize the Subscription.  
  
## Remarks and Restrictions  
 Only one\-way transactional replication is supported. Peer\-to\-peer transactional replication is not supported.  
  
 Memory\-optimized tables cannot be published.  
  
 Replication tables on the distributor cannot be configured as memory\-optimized tables.  
  
 Merge replication cannot include memory\-optimized tables.  
  
 At the subscriber, tables involved in transactional replication can be configured as memory optimized tables, but the subscriber tables must meet the requirements of memory\-optimized tables. This requires the following restrictions.  
  
-   Tables replicated to memory\-optimized tables on a subscriber are limited to the 8060 bytes per row limit of memory\-optimized tables.  
  
-   Tables replicated to memory\-optimized tables on a subscriber are limited to the data types permitted in memory\-optimized tables. For more information, see [Supported Data Types for In-Memory OLTP](../../Topics\TopicNameNotContainA/Supported-Data-Types-for-In-Memory-OLTP.md).  
  
-   Foreign key, unique constraint, triggers, schema modifications, ROWGUIDCOL, computed columns, data compression, alias data types, versioning, and locks are not supported in memory\-optimized tables. See [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md) for information.  
  
##  <a name="Schema"></a> Modifying a schema file  
  
-   All columns in the key of an index must be specified as **NOT NULL**.  
  
-   If using the memory\-optimized table option `DURABILITY = SCHEMA_AND_DATA` the table must have a nonclustered primary key index.  
  
-   ANSI\_PADDING must be ON.  
  
## See Also  
 [Replication Features and Tasks](../../Topics\TopicNameNotContainA/Replication-Features-and-Tasks.md)  
  
  