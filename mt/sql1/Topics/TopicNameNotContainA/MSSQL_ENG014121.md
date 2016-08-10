---
title: "MSSQL_ENG014121"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG014121
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14121|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Could not drop the Distributor '%s'. This Distributor has associated distribution databases.|  
  
## Explanation  
 A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance that is configured as a Distributor cannot be removed from the role of Distributor because there are distribution databases associated with the instance. This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.  
  
## User Action  
 To find the names of any Publishers and distribution databases associated with this Distributor, execute [sp_helpdistpublisher (Transact-SQL)](assetId:///f207c22d-8fb2-4756-8a9d-6c51d6cd3470) from any database on the Distributor.  
  
 Execute [sp_dropdistributiondb (Transact-SQL)](assetId:///b6dd1846-2259-4d29-93af-a70a5d25a0c5) for any distribution databases associated with this Distributor. After all distribution database associations are removed, you can disable distribution.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)   
 [Configure Distribution](../../Topics/TopicNameNotContainA/Configure-Distribution.md)