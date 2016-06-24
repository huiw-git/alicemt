---
title: High Availability Solutions (SQL Server)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
---
# High Availability Solutions (SQL Server)
  This topic introduces several [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] high-availability solutions that improve the availability of servers or databases. A high-availability solution masks the effects of a hardware or software failure and maintains the availability of applications so that the perceived downtime for users is minimized.    
    
   
>  **Note!** Want to know which [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] editions support a given high availability solution? See the "High Availability (Always On)" section of [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).    
     
    
##  <a name="TermsAndDefinitions"></a> Overview of SQL Server High-Availability Solutions    
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] provides several options for creating high availability for a server or database. The high-availability options include the following:    
    
*  Always On Failover Cluster Instances    
 As part of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Always On offering, Always On Failover Cluster Instances leverages Windows Server Failover Clustering (WSFC) functionality to provide local high availability through redundancy at the server-instance level—a *failover cluster instance* (FCI). An FCI is a single instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] that is installed across Windows Server Failover Clustering (WSFC) nodes and, possibly, across multiple subnets. On the network, an FCI appears to be an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] running on a single computer, but the FCI provides failover from one WSFC node to another if the current node becomes unavailable.    
    
 For more information, see [Always On Failover Cluster Instances &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Always-On-Failover-Cluster-Instances--SQL-Server-.md).    
    
*  [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)]    
 [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] is an enterprise-level high-availability and disaster recovery solution introduced in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/includes/ssSQL11_md.md)] to enable you to maximize availability for one or more user databases. [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] requires that the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] instances reside on Windows Server Failover Clustering (WSFC) nodes. For more information, see [Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Always-On-Availability-Groups--SQL-Server-.md).    
    
  
>  **Note!** An FCI can leverage [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] to provide remote disaster recovery at the database level. For more information, see [Failover Clustering and Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Failover-Clustering-and-Always-On-Availability-Groups--SQL-Server-.md).    
    
*  Database mirroring. **Note!** [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/includes/ssNoteDepFutureAvoid_md.md)] We recommend that you use [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] instead.     
Database mirroring is a solution to increase database availability by supporting almost instantaneous failover. Database mirroring can be used to maintain a single standby database, or *mirror database*, for a corresponding production database that is referred to as the *principal database*. For more information, see [Database Mirroring &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Database-Mirroring--SQL-Server-.md).    
    
*  Log shipping    
 Like [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] and database mirroring, log shipping operates at the database level. You can use log shipping to maintain one or more warm standby databases (referred to as *secondary databases*) for a single production database that is referred to as the *primary database*. For more information about log shipping, see [About Log Shipping &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md).    
    
##  <a name="RecommendedSolutions"></a> Recommended Solutions for Using SQL Server to Protect Data    
 Our recommendation for providing data protection for your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] environment:    
    
-   For data protection through a third-party shared disk solution (a SAN), we recommend that you use Always On Failover Cluster Instances.    
    
-   For data protection through [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], we recommend that you use [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)].    
    
       >  We recommend using log shipping if you are running an edition of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] that does not support [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)]. For information about which editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] support [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)], see the "High Availability (Always On)" section of [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).    
    
## See Also    
 [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../Topics/TopicNameNotContainA/Windows-Server-Failover-Clustering--WSFC--with-SQL-Server.md)     
 [Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](../Topic/Database%20Mirroring:%20Interoperability%20and%20Coexistence%20\(SQL%20Server\).md)     
 [Deprecated Database Engine Features in SQL Server 2016](../../Topics/TopicNameNotContainA/Deprecated-Database-Engine-Features-in-SQL-Server-2016.md)    
    
  