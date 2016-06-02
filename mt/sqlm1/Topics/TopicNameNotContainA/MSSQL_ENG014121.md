---
title: MSSQL_ENG014121
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
---
# MSSQL_ENG014121
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14121|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Could not drop the Distributor '%s'. This Distributor has associated distribution databases.|  
  
## Explanation  
 A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance that is configured as a Distributor cannot be removed from the role of Distributor because there are distribution databases associated with the instance. This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.  
  
## User Action  
 To find the names of any Publishers and distribution databases associated with this Distributor, execute [sp_helpdistpublisher &#40;Transact-SQL&#41;](../Topic/sp_helpdistpublisher%20\(Transact-SQL\).md) from any database on the Distributor.  
  
 Execute [sp_dropdistributiondb &#40;Transact-SQL&#41;](../Topic/sp_dropdistributiondb%20\(Transact-SQL\).md) for any distribution databases associated with this Distributor. After all distribution database associations are removed, you can disable distribution.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)   
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)  
  
  