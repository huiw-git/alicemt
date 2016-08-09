---
title: "Fail Over to a Log Shipping Secondary (SQL Server)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edfe5d59-4287-49c1-96c9-dd56212027bc
caps.latest.revision: 32
caps.handback.revision: 0
manager: jhubbard
---
# Fail Over to a Log Shipping Secondary (SQL Server)
Failing over to a log shipping secondary is useful if the primary server instance fails or requires maintenance.  
  
## Preparing for a Controlled Failover  
 Typically, the primary and secondary databases are unsynchronized, because the primary database continues to be updated after its latest backup job. Also, in some cases, recent transaction log backups have not been copied to the secondary server instances, or some copied log backups might still not have been applied to the secondary database. We recommend that you begin by synchronizing all of the secondary databases with the primary database, if possible.  
  
 For information about log shipping jobs, see [About Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md).  
  
## Failing Over  
 To fail over to a secondary database:  
  
1.  Copy any uncopied backup files from the backup share to the copy destination folder of each secondary server.  
  
2.  Apply any unapplied transaction log backups in sequence to each secondary database. For more information, see [Apply Transaction Log Backups (SQL Server)](../../Topics/TopicNameNotContainA/Apply-Transaction-Log-Backups--SQL-Server-.md).  
  
3.  If the primary database is accessible, back up the active transaction log and apply the log backup to the secondary databases.  
  
     If the original primary server instance is not damaged, back up the tail of the transaction log of the primary database using WITH NORECOVERY. This leaves the database in the restoring state and therefore unavailable to users. Eventually you will be able to roll this database forward by applying transaction log backups from the replacement primary database.  
  
     For more information, see [Transaction Log Backups (SQL Server)](../../Topics/TopicNameNotContainA/Transaction-Log-Backups--SQL-Server-.md).  
  
4.  After the secondary servers are synchronized, you can fail over to whichever one you prefer by recovering its secondary database and redirecting clients to that server instance. Recovering puts the database into a consistent state and brings it online.  
  
    > [!NOTE]  
    >  When you make a secondary database available, you should ensure that its metadata is consistent with the metadata of the original primary database. For more information, see [Manage Metadata When Making a Database Available on Another Server Instance (SQL Server)](../../Topics/TopicNameContainA/Manage-Metadata-When-Making-a-Database-Available-on-Another-Server-Instance--SQL-Server-.md).  
  
5.  After you have recovered a secondary database, you can reconfigure it to act as a primary database for other secondary databases.  
  
     If no other secondary database is available, see [Configure Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Log-Shipping--SQL-Server-.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Change Roles Between Primary and Secondary Log Shipping Servers (SQL Server)](../../Topics/TopicNameNotContainA/Change-Roles-Between-Primary-and-Secondary-Log-Shipping-Servers--SQL-Server-.md)  
  
-   [Management of Logins and Jobs After Role Switching (SQL Server)](../../Topics/TopicNameNotContainA/Management-of-Logins-and-Jobs-After-Role-Switching--SQL-Server-.md)  
  
## See Also  
 [Log Shipping Tables and Stored Procedures](../../Topics/TopicNameNotContainA/Log-Shipping-Tables-and-Stored-Procedures.md)   
 [About Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md)   
 [Tail-Log Backups (SQL Server)](../../Topics/TopicNameNotContainA/Tail-Log-Backups--SQL-Server-.md)