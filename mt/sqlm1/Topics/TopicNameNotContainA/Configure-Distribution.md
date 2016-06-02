---
title: Configure Distribution
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
---
# Configure Distribution
  The Distributor is a server that contains the distribution database, which stores metadata and history data for all types of replication and transactions for transactional replication. To set up replication, you must configure a Distributor. Each Publisher can be assigned to only a single Distributor instance, but multiple publishers can share a Distributor. The Distributor uses these additional resources on the server where it is located:  
  
-   Additional disk space if the snapshot files for the publication are stored on the Distributor \(which they typically are\).  
  
-   Additional disk space to store the distribution database.  
  
-   Additional processor usage by replication agents for push subscriptions running on the Distributor.  
  
 The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server. When you configure the Distributor, you specify the following:  
  
-   A snapshot folder, which is used, by default, for all Publishers that use this Distributor. Ensure that this folder is already shared and has the appropriate permissions set. For more information, see [Secure the Snapshot Folder](../../Topics\TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
-   A name and file locations for the distribution database. The distribution database cannot be renamed after it is created. To use a different name for the database, you must disable distribution and reconfigure it.  
  
-   Any Publishers authorized to use the Distributor. If you specify Publishers other than the instance on which the Distributor runs, you must also specify a password for the connections the Publishers make to the remote Distributor.  
  
 For transactional replication, after you configure distribution, we recommend that you:  
  
-   Size the distribution database appropriately. Test replication with a typical load for your system to determine how much space is required to store commands. Ensure the database is large enough to store commands without having to auto\-grow frequently. For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
-   Set the **sync with backup** option on the distribution database. For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../../Topics\TopicNameNotContainA/Strategies-for-Backing-Up-and-Restoring-Snapshot-and-Transactional-Replication.md) and [Enable Coordinated Backups for Transactional Replication &#40;Replication Transact-SQL Programming&#41;](../Topic/Enable%20Coordinated%20Backups%20for%20Transactional%20Replication%20\(Replication%20Transact-SQL%20Programming\).md).  
  
## Local and Remote Distributors  
 By default, the Distributor is the same server as the Publisher \(a local Distributor\), but it can also be a separate server from the Publisher \(a remote Distributor\). Typically, you would choose to use a remote Distributor if you want to:  
  
-   Offload processing to another computer if you want minimal impact from replication on the Publisher \(for example, if the Publisher is an OLTP server\).  
  
-   Configure a centralized Distributor for multiple Publishers.  
  
 Remote Distributors are more common in transactional replication than they are in merge replication for two reasons:  
  
-   The Distributor plays a larger role in transactional replication because all replicated transactions are written to and read from the distribution database.  
  
-   Merge replication topologies typically use pull subscriptions, so agents run at each Subscriber, rather than all running at the Distributor. For more information, see [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md). In most cases, you should use a local Distributor for merge replication.  
  
 To configure publishing and distribution, see [Configure Publishing and Distribution](../../Topics\TopicNameNotContainA/Configure-Publishing-and-Distribution.md).  
  
 To modify Publisher and Distributor properties, see [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md).  
  
## See Also  
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Secure the Distributor](../../Topics\TopicNameNotContainA/Secure-the-Distributor.md)  
  
  