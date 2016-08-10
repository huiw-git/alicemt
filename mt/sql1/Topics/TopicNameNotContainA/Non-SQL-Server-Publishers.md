---
title: "Non-SQL Server Publishers"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: 32
manager: jhubbard
---
# Non-SQL Server Publishers
Publishing data from non-[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] sources allows you to consolidate data in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can subscribe to snapshot or transactional data published from an Oracle database. For more information about publishing from Oracle, see [Oracle Publishing Overview](../../Topics/TopicNameNotContainA/Oracle-Publishing-Overview.md).  
  
 Heterogeneous replication to non-SQL Server subscribers is deprecated. Oracle Publishing is deprecated. To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureAvoid_md.md)]  
  
 Publishing from non-[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases is ideal for the following scenarios:  
  
|Scenario|Description|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] .NET Framework application deployments|Develop with [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database.|  
|Data warehousing staging servers|Keep [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database.|  
|Migration to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]|Test your application in real time against [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] while replicating the source system's changes. Switch to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] when satisfied with the migration.|  
  
## See Also  
 [Heterogeneous Database Replication](../../Topics/TopicNameNotContainA/Heterogeneous-Database-Replication.md)