---
title: Heterogeneous Database Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
---
# Heterogeneous Database Replication
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports the following heterogeneous scenarios for transactional and snapshot replication:  
  
-   Publishing data from Oracle to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   Publishing data from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers.  
  
 Heterogeneous replication to non\-SQL Server subscribers is deprecated. Oracle Publishing is deprecated. To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)]  
  
## Publishing Data from Oracle  
 You can use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to publish data from Oracle with most of the same features and ease\-of\-use as [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] snapshot and transactional replication. Publishing data from Oracle is ideal for the following scenarios:  
  
|Scenario|Description|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] .NET Framework application deployments|Develop with [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] while operating on data replicated from a non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database.|  
|Data warehousing staging servers|Keep [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] staging databases synchronized with a non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database.|  
|Migration to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|Test your application in real time against [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] while replicating the source system's changes. Switch to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] when satisfied with the migration.|  
  
 For more information, see [Oracle Publishing Overview](../../Topics\TopicNameNotContainA/Oracle-Publishing-Overview.md).  
  
## Publishing Data to Non\-SQL Server Subscribers  
 The following non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases are supported as Subscribers to snapshot and transactional publications:  
  
-   Oracle for all platforms that Oracle supports.  
  
-   IBM DB2 for AS400, MVS, Unix, Linux, and Windows.  
  
 For more information, see [Non-SQL Server Subscribers](../../Topics\TopicNameNotContainA/Non-SQL-Server-Subscribers.md).  
  
  