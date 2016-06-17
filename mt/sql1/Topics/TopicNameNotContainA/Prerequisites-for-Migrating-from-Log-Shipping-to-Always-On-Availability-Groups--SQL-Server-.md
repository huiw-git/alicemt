---
title: Prerequisites for Migrating from Log Shipping to Always On Availability Groups (SQL Server)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
---
# Prerequisites for Migrating from Log Shipping to Always On Availability Groups (SQL Server)
  This topic describes the prerequisites for converting a log shipping primary database along with one or more of its secondary databases to an Always On primary database and secondary database\(s\).  
  
> [!NOTE]  
>  You can configure any primary or secondary database \(possibly readable\) in an availability group as a log shipping primary database.  
  
 **In This Topic:**  
  
-   [Availability Group Prerequisites](#AGPrereqsRealAddress)  
  
-   [Log Shipping Prerequisites](#LogShipPrereqs)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="AGPrereqsRealAddress"></a> Availability Group Prerequisites  
 To allow backup jobs to run on the primary replica of the availability group, use the following Always On Availability Groups backup settings:  
  
|Property|Setting|  
|--------------|-------------|  
|Automated backup preference of availability group|Only on the primary replica|  
|Backup priority of the primary replica.|\>0|  
  
 **For more information:**  
  
 [View Availability Group Properties &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/View-Availability-Group-Properties--SQL-Server-.md)  
  
 [Configure Backup on Availability Replicas &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Configure-Backup-on-Availability-Replicas--SQL-Server-.md)  
  
##  <a name="LogShipPrereqs"></a> Log Shipping Prerequisites  
  
-   The log shipping primary database must reside on the instance of [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] that hosts the initial\/current primary replica of the availability group.  
  
-   For a given log shipping secondary database to be converted to an Always On secondary database, it must:  
  
    -   Use the same name as the primary database.  
  
    -   Reside on a server instance that hosts a secondary replica for the availability group.  
  
 Once the backup job has run on the primary database, disable the backup job, and once the restore job has run on a given secondary database, disable the restore job.  
  
 After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you need to re\-configure the automated backup preference of the availability group.  
  
 **For more information:**  
  
 [Converting a logshipping configuration to Availability Group](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) \(a SQL Server blog\)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **Log shipping**  
  
-   [Upgrading Log Shipping to SQL Server 2016 &#40;Transact-SQL&#41;](../../Topics/TopicNameNotContainA/Upgrading-Log-Shipping-to-SQL-Server-2016--Transact-SQL-.md)  
  
-   [Remove Log Shipping &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Remove-Log-Shipping--SQL-Server-.md)  
  
 **Always On Availability Groups**  
  
-   [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-Availability-Group-Wizard--SQL-Server-Management-Studio-.md)  
  
-   [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-New-Availability-Group-Dialog-Box--SQL-Server-Management-Studio-.md)  
  
-   [Create an Availability Group &#40;Transact-SQL&#41;](../../Topics/TopicNameNotContainA/Create-an-Availability-Group--Transact-SQL-.md)  
  
-   [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../Topics/TopicNameNotContainA/Create-an-Availability-Group--SQL-Server-PowerShell-.md)  
  
-   [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../../Topics/TopicNameContainA/Join-a-Secondary-Database-to-an-Availability-Group--SQL-Server-.md)  
  
-   [Configure Backup on Availability Replicas &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Configure-Backup-on-Availability-Replicas--SQL-Server-.md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Blogs:**  
  
     [Converting a logshipping configuration to Availability Group](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx)  
  
     [Add a Log Shipping Primary Database and Secondary Database\(s\) to an Existing Availability Group](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/01/use-log-shipping-to-prepare-secondary-databases-for-an-existing-availability-group.aspx)  
  
     [SQL Server Always On Team Blogs: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server Engineers Blogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Whitepapers:**  
  
     [Migration Guide: Migrating to Always On Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping](http://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft White Papers for SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server Customer Advisory Team Whitepapers](http://sqlcat.com/)  
  
## See Also  
 [About Log Shipping &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Monitoring of Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Monitoring-of-Availability-Groups--SQL-Server-.md)  
  
  