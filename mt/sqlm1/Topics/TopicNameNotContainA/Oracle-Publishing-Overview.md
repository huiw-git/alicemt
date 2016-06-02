---
title: Oracle Publishing Overview
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
---
# Oracle Publishing Overview
  Beginning with [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], you can include Oracle Publishers in your replication topology, starting with Oracle version 9i. Publishing servers can be deployed on any Oracle supported hardware and operating system. The feature is built on the well\-established foundation of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] snapshot replication and transactional replication, providing similar performance and usability.  
  
 Oracle Publishing is deprecated. Heterogeneous replication to non\-SQL Server subscribers is deprecated. To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)]  
  
## Snapshot Replication for Oracle  
 Oracle snapshot publications are implemented in a manner similar to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] snapshot publications. When the Snapshot Agent runs for an Oracle publication, it connects to the Oracle Publisher and processes each table in the publication. When processing each table, the agent retrieves the table rows and creates schema scripts, which are then stored on the publication's snapshot share. The entire set of data is created each time the Snapshot Agent runs, so change tracking triggers are not added to the Oracle tables as they are with transactional replication. Snapshot replication provides a convenient way to migrate data with minimal impact on the publishing system.  
  
## Transactional Replication for Oracle  
 Oracle transactional publications are implemented using the transactional publishing architecture of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]; however, changes are tracked using a combination of database triggers on the Oracle database and the Log Reader Agent. Subscribers to an Oracle transactional publication are automatically initialized using snapshot replication; subsequent changes are tracked and delivered to Subscribers as they occur via the Log Reader Agent.  
  
 When an Oracle publication is created, triggers and tracking tables are created for each published table within the Oracle database. When data changes are made to the published tables, the database triggers on the tables fire and insert information into the replication tracking tables for each modified row. The Log Reader Agent on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor then moves the data change information from the tracking tables to the distribution database on the Distributor. Finally, as in standard transactional replication, the Distribution Agent moves changes from the Distributor to the Subscribers.  
  
## See Also  
 [Configure an Oracle Publisher](../../Topics\TopicNameNotContainA/Configure-an-Oracle-Publisher.md)   
 [Glossary of Terms for Oracle Publishing](../../Topics\TopicNameNotContainA/Glossary-of-Terms-for-Oracle-Publishing.md)   
 [Heterogeneous Database Replication](../../Topics\TopicNameNotContainA/Heterogeneous-Database-Replication.md)  
  
  