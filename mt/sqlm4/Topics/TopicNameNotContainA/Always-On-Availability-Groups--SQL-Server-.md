---
title: Always On Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa427606-8422-4656-b205-c9e665ddc8c1
---
# Always On Availability Groups (SQL Server)
  The [!INCLUDE[ssHADR](../../Token/Other/ssHADR_md.md)] feature is a high\-availability and disaster\-recovery solution that provides an enterprise\-level alternative to database mirroring. Introduced in [!INCLUDE[ssSQL11](../../Token/Other/ssSQL11_md.md)], [!INCLUDE[ssHADR](../../Token/Other/ssHADR_md.md)] maximizes the availability of a set of user databases for an enterprise. An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together. An availability group supports a set of read\-write primary databases and one to eight sets of corresponding secondary databases. Optionally, secondary databases can be made available for read\-only access and\/or some backup operations.  
  
 An availability group fails over at the level of an availability replica. Failovers are not caused by database issues such as a database becoming suspect due to a loss of a data file, deletion of a database, or corruption of a transaction log.  
  
 **In this Topic:**  
  
-   [Benefits](#Benefits)  
  
-   [Terms and Definitions](#TermsAndDefinitions)  
  
-   [Interoperability and Coexistence with Other Database Engine Features](#Interoperability)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="Benefits"></a> Benefits  
 [!INCLUDE[ssHADR](../../Token/Other/ssHADR_md.md)] provides a rich set of options that improve database availability and that enable improved resource use. The key components are as follows:  
  
-   Supports up to nine availability replicas. An *availability replica* is an instantiation of an availability group that is hosted by a specific instance of SQL Server and maintains a local copy of each availability database that belongs to the availability group. Each availability group supports one primary replica and up to eight secondary replicas. For more information, see [Overview of Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md).  
  
    > [!IMPORTANT]  
    >  Each availability replica must reside on a different node of a single Windows Server Failover Clustering \(WSFC\) cluster. For more information about prerequisites, restrictions, and recommendations for availability groups, see [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Prerequisites,-Restrictions,-and-Recommendations-for-Always-On-Availability-Groups--SQL-Server-.md).  
  
-   Supports alternative availability modes, as follows:  
  
    -   *Asynchronous\-commit mode*. This availability mode is a disaster\-recovery solution that works well when the availability replicas are distributed over considerable distances.  
  
    -   *Synchronous\-commit mode*. This availability mode emphasizes high availability and data protection over performance, at the cost of increased transaction latency. A given availability group can support up to three synchronous\-commit availability replicas, including the current primary replica.  
  
     For more information, see [Availability Modes &#40;Always On Availability Groups&#41;](../../Topics/TopicNameNotContainA/Availability-Modes--Always-On-Availability-Groups-.md).  
  
-   Supports several forms of availability\-group failover:  automatic failover, planned manual failover \(generally referred as simply "manual failover"\), and forced manual failover \(generally referred as simply "forced failover"\). For more information, see [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../../Topics/TopicNameNotContainA/Failover-and-Failover-Modes--Always-On-Availability-Groups-.md).  
  
-   Enables you to configure a given availability replica to support either or both of the following active\-secondary capabilities:  
  
    -   Read\-only connection access which enables read\-only connections to the replica to access and read its databases when it is running as a secondary replica. For more information, see [Active Secondaries: Readable Secondary Replicas &#40;Always On Availability Groups&#41;](../Topic/Active%20Secondaries:%20Readable%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md).  
  
    -   Performing backup operations on its databases when it is running as a secondary replica. For more information, see [Active Secondaries: Backup on Secondary Replicas &#40;Always On Availability Groups&#41;](../Topic/Active%20Secondaries:%20Backup%20on%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md).  
  
     Using active secondary capabilities improves your IT efficiency and reduce cost through better resource utilization of secondary hardware. In addition, offloading read\-intent applications and backup jobs to secondary replicas helps to improve performance on the primary replica.  
  
-   Supports an availability group listener for each availability group. An *availability group listener* is a server name to which clients can connect in order to access a database in a primary or secondary replica of an Always On availability group. Availability group listeners direct incoming connections to the primary replica or to a read\-only secondary replica. The listener provides fast application failover after an availability group fails over. For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Availability-Group-Listeners,-Client-Connectivity,-and-Application-Failover--SQL-Server-.md).  
  
-   Supports a flexible failover policy for greater control over availability\-group failover. For more information, see [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../../Topics/TopicNameNotContainA/Failover-and-Failover-Modes--Always-On-Availability-Groups-.md).  
  
-   Supports automatic page repair for protection against page corruption. For more information, see [Automatic Page Repair &#40;Availability Groups: Database Mirroring&#41;](../Topic/Automatic%20Page%20Repair%20\(Availability%20Groups:%20Database%20Mirroring\).md).  
  
-   Supports encryption and compression, which provide a secure, high performing transport.  
  
-   Provides an integrated set of tools to simplify deployment and management of availability groups, including:  
  
    -   [!INCLUDE[tsql](../../Token/Other/tsql_md.md)] DDL statements for creating and managing availability groups. For more information, see [Overview of Transact-SQL Statements for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-Transact-SQL-Statements-for-Always-On-Availability-Groups--SQL-Server-.md).  
  
    -   [!INCLUDE[ssManStudioFull](../../Token/Other/ssManStudioFull_md.md)] tools, as follows:  
  
        -   The [!INCLUDE[ssAoNewAgWiz](../../Token/Other/ssAoNewAgWiz_md.md)] creates and configures an availability group. In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them. For more information, see [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-New-Availability-Group-Dialog-Box--SQL-Server-Management-Studio-.md).  
  
        -   The [!INCLUDE[ssAoAddDbWiz](../../Token/Other/ssAoAddDbWiz_md.md)] adds one or more primary databases to an existing availability group. In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them. For more information, see [Use the Add Database to Availability Group Wizard \(SQL Server\)](../../Topics/TopicNameNotContainA/Use-the-Add-Database-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md).  
  
        -   The [!INCLUDE[ssAoAddRepWiz](../../Token/Other/ssAoAddRepWiz_md.md)] adds one or more secondary replicas to an existing availability group. In some environments, this wizard can also automatically prepare the secondary databases and start data synchronization for each of them. For more information, see [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-Add-Replica-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md).  
  
        -   The [!INCLUDE[ssAoFoAgWiz](../../Token/Other/ssAoFoAgWiz_md.md)] initiates a manual failover on an availability group. Depending on the configuration and state of the secondary replica that you specify as the failover target, the wizard can perform either a planned or forced manual failover. For more information, see [Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-Fail-Over-Availability-Group-Wizard--SQL-Server-Management-Studio-.md).  
  
    -   The [!INCLUDE[ssAoDash](../../Token/Other/ssAoDash_md.md)] monitors Always On availability groups, availability replicas, and availability databases and evaluates results for Always On policies. For more information, see [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-Always-On-Dashboard--SQL-Server-Management-Studio-.md).  
  
    -   The Object Explorer Details pane displays basic information about existing availability groups. For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Use-the-Object-Explorer-Details-to-Monitor-Availability-Groups--SQL-Server-Management-Studio-.md).  
  
    -   PowerShell cmdlets. For more information, see [Overview of PowerShell Cmdlets for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-PowerShell-Cmdlets-for-Always-On-Availability-Groups--SQL-Server-.md).  
  
##  <a name="TermsAndDefinitions"></a> Terms and Definitions  
 availability group  
 A container for a set of databases, *availability databases*, that fail over together.  
  
 availability database  
 A database that belongs to an availability group. For each availability database, the availability group maintains a single read\-write copy \(the *primary database*\) and one to eight read\-only copies \(*secondary databases*\).  
  
 primary database  
 The read\-write copy of an availability database.  
  
 secondary database  
 A read\-only copy of an availability database.  
  
 availability replica  
 An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] and maintains a local copy of each availability database that belongs to the availability group. Two types of availability replicas exist: a single *primary replica* and one to eight *secondary replicas*.  
  
 primary replica  
 The availability replica that makes the primary databases available for read\-write connections from clients and, also, sends transaction log records for each primary database to every secondary replica.  
  
 secondary replica  
 An availability replica that maintains a secondary copy of each availability database, and serves as a potential failover targets for the availability group. Optionally, a secondary replica can support read\-only access to secondary databases can support creating backups on secondary databases.  
  
 availability group listener  
 A server name to which clients can connect in order to access a database in a primary or secondary replica of an Always On availability group. Availability group listeners direct incoming connections to the primary replica or to a read\-only secondary replica.  
  
> [!NOTE]  
>  For more information, see [Overview of Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md).  
  
##  <a name="Interoperability"></a> Interoperability and Coexistence with Other Database Engine Features  
 [!INCLUDE[ssHADR](../../Token/Other/ssHADR_md.md)] can be used with the following features or components of [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)]:  
  
-   [About Change Data Capture &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/About-Change-Data-Capture--SQL-Server-.md)  
  
-   [About Change Tracking &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/About-Change-Tracking--SQL-Server-.md)  
  
-   [Contained databases](../../Topics/TopicNameNotContainA/Contained-Databases.md)  
  
-   [Database encryption](../../Topics/TopicNameNotContainA/Transparent-Data-Encryption--TDE-.md)  
  
-   [Database snapshots](../../Topics/TopicNameNotContainA/Database-Snapshots-with-Always-On-Availability-Groups--SQL-Server-.md)  
  
-   [FILESTREAM](../../Topics/TopicNameNotContainA/FILESTREAM--SQL-Server-.md)  
  
-   [FileTable](../../Topics/TopicNameNotContainA/FileTables--SQL-Server-.md)  
  
-   [Log shipping](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md)  
  
-   [Remote Blob Store \(RBS\)](../../Topics/TopicNameNotContainA/Remote-Blob-Store--RBS---SQL-Server-.md)  
  
-   [Replication](../../Topics/TopicNameNotContainA/SQL-Server-Replication.md)  
  
-   [Service Broker](../../Topics/TopicNameNotContainA/SQL-Server-Service-Broker.md)  
  
-   [SQL Server Agent](../Topic/SQL%20Server%20Agent.md)  
  
-   [Reporting Services](../../Topics/TopicNameNotContainA/Reporting-Services-with-Always-On-Availability-Groups--SQL-Server-.md)  
  
> [!WARNING]  
>  For information about restrictions and limitations for using other features with [!INCLUDE[ssHADR](../../Token/Other/ssHADR_md.md)], see [Always On Availability Groups: Interoperability &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Getting Started with Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Getting-Started-with-Always-On-Availability-Groups--SQL-Server-.md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Blogs:**  
  
     [SQL Server Always On Team Blogs: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server Engineers Blogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Videos:**  
  
     [Microsoft SQL Server Code\-Named "Denali" Always On Series,Part 1: Introducing the Next Generation High Availability Solution](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Code\-Named "Denali" Always On Series,Part 2: Building a Mission\-Critical High Availability Solution Using Always On](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepapers:**  
  
     [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft White Papers for SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server Customer Advisory Team Whitepapers](http://sqlcat.com/)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Prerequisites,-Restrictions,-and-Recommendations-for-Always-On-Availability-Groups--SQL-Server-.md)   
 [Configuration of a Server Instance for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameContainA/Configuration-of-a-Server-Instance-for-Always-On-Availability-Groups--SQL-Server-.md)   
 [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Creation-and-Configuration-of-Availability-Groups--SQL-Server-.md)   
 [Administration of an Availability Group &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Administration-of-an-Availability-Group--SQL-Server-.md)   
 [Monitoring of Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Monitoring-of-Availability-Groups--SQL-Server-.md)   
 [Overview of Transact-SQL Statements for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-Transact-SQL-Statements-for-Always-On-Availability-Groups--SQL-Server-.md)   
 [Overview of PowerShell Cmdlets for Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-PowerShell-Cmdlets-for-Always-On-Availability-Groups--SQL-Server-.md)  
  
  