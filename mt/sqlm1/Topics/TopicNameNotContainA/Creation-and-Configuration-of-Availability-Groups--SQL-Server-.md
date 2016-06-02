---
title: Creation and Configuration of Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
---
# Creation and Configuration of Availability Groups (SQL Server)
  The topics in this section explain how to deploy a [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] implementation on instances of [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] that reside on different Windows Server Failover Clustering \(WSFC\) nodes within a single WSFC failover cluster.  
  
 Before you create your first availability group, we strongly recommend that you familiarize yourself with the information in the following topics:  
  
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
 This topic describes the prerequisites, restrictions, and recommendations for computers; WSFC nodes; instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]; availability groups, replicas, and databases. This topic also contains information about security considerations.  
  
 [Getting Started with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Getting%20Started%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
 Contains information about the steps for configuring a server instance, creating an availability group, configuring the availability group for client connections, managing availability groups, and monitoring availability groups.  
  
 **In this Topic:**  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To configure a server instance for [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)]**  
  
-   [Enable and Disable Always On Availability Groups &#40;SQL Server&#41;](../Topic/Enable%20and%20Disable%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
-   [Create a Database Mirroring Endpoint for Always On Availability Groups &#40;SQL Server PowerShell&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server%20PowerShell\).md)  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
 **To get started with configuring Always On Availability Groups**  
  
-   [Getting Started with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Getting%20Started%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
 **To create and configure a new availability group**  
  
-   [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Create an Availability Group &#40;Transact-SQL&#41;](../Topic/Create%20an%20Availability%20Group%20\(Transact-SQL\).md)  
  
-   [Create an Availability Group &#40;SQL Server PowerShell&#41;](../Topic/Create%20an%20Availability%20Group%20\(SQL%20Server%20PowerShell\).md)  
  
-   [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20New%20Availability%20Group%20Dialog%20Box%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](../Topic/Specify%20the%20Endpoint%20URL%20When%20Adding%20or%20Modifying%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
-   [Configure the Flexible Failover Policy to Control Conditions for Automatic Failover &#40;Always On Availability Groups&#41;](../Topic/Configure%20the%20Flexible%20Failover%20Policy%20to%20Control%20Conditions%20for%20Automatic%20Failover%20\(Always%20On%20Availability%20Groups\).md)  
  
-   [Configure Backup on Availability Replicas &#40;SQL Server&#41;](../Topic/Configure%20Backup%20on%20Availability%20Replicas%20\(SQL%20Server\).md)  
  
-   [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](../Topic/Configure%20Read-Only%20Access%20on%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;](../Topic/Configure%20Read-Only%20Routing%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Start Data Movement on an Always On Secondary Database &#40;SQL Server&#41;](../Topic/Start%20Data%20Movement%20on%20an%20Always%20On%20Secondary%20Database%20\(SQL%20Server\).md)  
  
-   [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Management of Logins and Jobs for the Databases of an Availability Group &#40;SQL Server&#41;](../Topic/Management%20of%20Logins%20and%20Jobs%20for%20the%20Databases%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
 **To troubleshoot**  
  
-   [Troubleshoot Always On Availability Groups Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Always%20On%20Availability%20Groups%20Configuration%20\(SQL%20Server\).md)  
  
-   [Troubleshoot a Failed Add-File Operation &#40;Always On Availability Groups&#41;](../Topic/Troubleshoot%20a%20Failed%20Add-File%20Operation%20\(Always%20On%20Availability%20Groups\).md)  
  
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
 [Administration of an Availability Group &#40;SQL Server&#41;](../Topic/Administration%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)   
 [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Policies%20for%20Operational%20Issues%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Monitoring of Availability Groups &#40;SQL Server&#41;](../Topic/Monitoring%20of%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Always On Availability Groups: Interoperability &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md)  
  
  