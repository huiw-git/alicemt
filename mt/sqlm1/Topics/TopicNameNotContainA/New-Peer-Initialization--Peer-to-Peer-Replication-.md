---
title: New Peer Initialization (Peer-to-Peer Replication)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
---
# New Peer Initialization (Peer-to-Peer Replication)
  Use the **New Peer Initialization** page to specify how peer databases were initialized. \(Peers must be initialized before you complete this wizard.\) Peers are initialized manually or by using the **initialize with backup** functionality that is provided by transactional replication. \(Peer\-to\-peer transactional replication does not support initializing peers by using a snapshot.\) If different peers have to be initialized using different methods, you must add the peers separately by running the wizard multiple times.  
  
## Options  
 **Specify how the new peer database\(s\) was initialized**  
 The schema and data for all published objects must be present at each peer. Select one of the following options:  
  
-   Select the first option if you have manually created the schema for published objects or you have restored a backup, and no data changes have been made at the first publication database since the backup was taken. If you created the schema manually, you must ensure that all required data is present at each peer. This option corresponds to a value of **replication support only** for the subscription property **sync\_type**.  
  
-   Select the second option if you have restored a backup, and data changes have been made at the first publication database since the backup was taken. Replication must now deliver changes from the first publication database that were not included in the backup. This option corresponds to a value of **initialize with backup** for the subscription property **sync\_type**.  
  
     When a publication is enabled for peer\-to\-peer replication, the **allow\_initialize\_from\_backup** publication property is set. Replication immediately starts to track changes in the first publication database. Therefore, these changes can be delivered to a restored database at one or more peers if the **initialize with backup** option is selected. Click the **Browse** button to locate the backup used, and replication will read the log sequence number \(LSN\) from the backup. All changes in the first publication database that have a higher LSN will be delivered to each peer.  
  
     This option might not be available if you are creating or adding to a topology that includes [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]. The following table shows whether the option is available when you are adding a node to an existing topology.  
  
    |New node|First node|Additional nodes|Option|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|Disabled|  
    |[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|None|Disabled|  
    |[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|Disabled|  
    |[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|None|Enabled|  
    |[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|None|Enabled|  
    |[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|Enabled|  
    |[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|None|Enabled|  
  
## See Also  
 [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../Topic/Administer%20a%20Peer-to-Peer%20Topology%20\(Replication%20Transact-SQL%20Programming\).md)   
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)  
  
  