---
title: MSSQL_ENG021330
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
---
# MSSQL_ENG021330
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21330|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Failed to create a sub\-directory under the replication working directory.\(%ls\)|  
  
## Explanation  
 This error can occur when a subscription is initialized manually, and there is a problem creating the directory in which replication scripts are stored. The error can be caused by a permissions issue: when a subscription is initialized without using a snapshot, the account under which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service runs at the Publisher must have write permissions on the snapshot folder at the Distributor.  
  
## User Action  
 Ensure that the correct path has been specified for the snapshot folder and that the account under which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service runs at the Publisher has sufficient permissions.  
  
## See Also  
 [Specify the Default Snapshot Location &#40;SQL Server Management Studio&#41;](../Topic/Specify%20the%20Default%20Snapshot%20Location%20\(SQL%20Server%20Management%20Studio\).md)   
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)   
 [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md)  
  
  