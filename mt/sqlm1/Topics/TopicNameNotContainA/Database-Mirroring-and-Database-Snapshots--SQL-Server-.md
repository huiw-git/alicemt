---
title: Database Mirroring and Database Snapshots (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0bf1be90-7ce4-484c-aaa7-f8a782f57c5f
---
# Database Mirroring and Database Snapshots (SQL Server)
  You can take advantage of a mirror database that you are maintaining for availability purposes to offload reporting. To use a mirror database for reporting, you can create a database snapshot on the mirror database and direct client connection requests to the most recent snapshot. A database snapshot is a static, read\-only, transaction\-consistent snapshot of its source database as it existed at the moment of the snapshot's creation. To create a database snapshot on a mirror database, the database must be in the synchronized mirroring state.  
  
 Unlike the mirror database itself, a database snapshot is accessible to clients. As long as the mirror server is communicating with the principal server, you can direct reporting clients to connect to a snapshot. Note that because a database snapshot is static, new data is not available. To make relatively recent data available to your users, you must create a new database snapshot periodically and have applications direct incoming client connections to the newest snapshot.  
  
 A new database snapshot is almost empty, but it grows over time as more and more database pages are updated for the first time. Because every snapshot on a database grows incrementally in this way, each database snapshot consumes as much resources as a normal database. Depending on the configurations of the mirror server and principal server, having an excessive number of database snapshots on a mirror database might decrease performance on the principal database. Therefore, we recommend that you keep only a few relatively recent snapshots on your mirror databases. Typically, after you create a replacement snapshot, you should redirect incoming queries to the new snapshot and drop the earlier snapshot after any current queries complete.  
  
> [!NOTE]  
>  For more information about database snapshots, see [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md).  
  
 If role switching occurs, the database and its snapshots are restarted, temporarily disconnecting users. Afterwards, the database snapshots remain on the server instance where they were created, which has become the new principal database. Users can continue to use the snapshots after the failover. However, this places an additional load on the new principal server. If performance is a concern in your environment, we recommend that you create a snapshot on the new mirror database when it becomes available, redirect clients to the new snapshot, and drop all of the database snapshots from the former mirror database.  
  
> [!NOTE]  
>  For a dedicated reporting solution that scales out well, consider replication. For more information, see [SQL Server Replication](../../Topics\TopicNameNotContainA/SQL-Server-Replication.md).  
  
## Example  
 This example creates snapshots on a mirrored database.  
  
 Assume that the database of a database mirroring session is [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)]. This example creates three database snapshots on the mirror copy of the `AdventureWorks` database, which resides on the `F` drive. The snapshots are named `AdventureWorks_0600`, `AdventureWorks_1200`, and `AdventureWorks_1800` to identify their approximate creation times.  
  
1.  Create the first database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)].  
  
    ```  
    CREATE DATABASE AdventureWorks_0600  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_0600.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
2.  Create the second database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)]. Users who are still using `AdventureWorks_0600` can continue to use it.  
  
    ```  
    CREATE DATABASE AdventureWorks_1200  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1200.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     At this point, new client connections can be programmatically directed to the latest snapshot.  
  
3.  Create the third snapshot on the mirror [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)]. Users who are still using `AdventureWorks_0600` or `AdventureWorks_1200` can continue to use them.  
  
    ```  
    CREATE DATABASE AdventureWorks_1800  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1800.SNP')  
        AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     At this point, new client connections can be programmatically directed to the latest snapshot.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create a Database Snapshot &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Snapshot%20\(Transact-SQL\).md)  
  
-   [View a Database Snapshot &#40;SQL Server&#41;](../Topic/View%20a%20Database%20Snapshot%20\(SQL%20Server\).md)  
  
-   [Drop a Database Snapshot &#40;Transact-SQL&#41;](../Topic/Drop%20a%20Database%20Snapshot%20\(Transact-SQL\).md)  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [&#91;Top&#93;](#Top)  
  
## See Also  
 [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md)   
 [Connect Clients to a Database Mirroring Session &#40;SQL Server&#41;](../Topic/Connect%20Clients%20to%20a%20Database%20Mirroring%20Session%20\(SQL%20Server\).md)  
  
  