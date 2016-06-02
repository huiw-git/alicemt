---
title: Configuration of a Server Instance for Always On Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
---
# Configuration of a Server Instance for Always On Availability Groups (SQL Server)
  This topic contains information about the requirements for configuring an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to support [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
> [!IMPORTANT]  
>  For essential information about [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] prerequisites and restrictions for Windows Server Failover Clustering \(WSFC\) nodes and for instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
 **In this Topic:**  
  
-   [Terms and Definitions](#TermsAndDefinitions)  
  
-   [To Configure a Server Instance to Support Always On Availability Groups](#ConfigSI)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="TermsAndDefinitions"></a> Terms and Definitions  
 [Always On Availability Groups](../Topic/Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
 A high\-availability and disaster\-recovery solution that provides an enterprise\-level replacement for database mirroring. An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together.  
  
 availability replica  
 An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and that maintains a local copy of each availability database that belongs to the availability group. Two types of availability replicas exist: a single *primary replica* and one to four *secondary replicas*. The server instances that host the availability replicas for a given availability group must reside on different nodes of a single Windows Server Failover Clustering \(WSFC\) cluster.  
  
 [database mirroring endpoint](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)  
 An endpoint is a SQL Server object that enables SQL Server to communicate over the network. To participate in database mirroring and\/or [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] a server instance requires a special, dedicated endpoint. All mirroring and availability group connections on a server instance use the same database mirroring endpoint. This endpoint is a special\-purpose endpoint used exclusively to receive these connections from other server instances.  
  
##  <a name="ConfigSI"></a> To Configure a Server Instance to Support Always On Availability Groups  
 To support [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], a server instance must reside on a node in the WSFC failover cluster that hosts the availability group, be [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] enabled, and possess a database mirroring endpoint.  
  
1.  Enable the Always On Availability Groups feature on every server instance that is to participate in one or more availability groups. A given server instance can host only a single availability replica for a given availability group.  
  
2.  Ensure that the server instance possesses a database mirroring endpoint.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To enable Always On Availability Groups**  
  
-   [Enable and Disable Always On Availability Groups &#40;SQL Server&#41;](../Topic/Enable%20and%20Disable%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
 **To determine whether a database mirroring endpoint exists**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../Topic/sys.database_mirroring_endpoints%20\(Transact-SQL\).md)  
  
 **To create a database mirroring endpoint**  
  
-   [Create a Database Mirroring Endpoint for Always On Availability Groups &#40;SQL Server PowerShell&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server%20PowerShell\).md)  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Blogs:**  
  
     [Always On \- HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
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
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)   
 [Always On Availability Groups: Interoperability &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md)   
 [Failover Clustering and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Failover%20Clustering%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../Topic/Windows%20Server%20Failover%20Clustering%20\(WSFC\)%20with%20SQL%20Server.md)   
 [Always On Failover Cluster Instances &#40;SQL Server&#41;](../Topic/Always%20On%20Failover%20Cluster%20Instances%20\(SQL%20Server\).md)  
  
  