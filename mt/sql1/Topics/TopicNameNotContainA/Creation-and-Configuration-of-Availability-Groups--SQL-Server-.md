---
title: "Creation and Configuration of Availability Groups (SQL Server)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Creation and Configuration of Availability Groups (SQL Server)
The topics in this section explain how to deploy a [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] implementation on instances of [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] that reside on different Windows Server Failover Clustering (WSFC) nodes within a single WSFC failover cluster.  
  
 Before you create your first availability group, we strongly recommend that you familiarize yourself with the information in the following topics:  
  
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Prerequisites--Restrictions--and-Recommendations-for-Always-On-Availability-Groups--SQL-Server-.md)  
 This topic describes the prerequisites, restrictions, and recommendations for computers; WSFC nodes; instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]; availability groups, replicas, and databases. This topic also contains information about security considerations.  
  
 [Getting Started with Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Getting-Started-with-Always-On-Availability-Groups--SQL-Server-.md)  
 Contains information about the steps for configuring a server instance, creating an availability group, configuring the availability group for client connections, managing availability groups, and monitoring availability groups.  
  
 **In this Topic:**  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To configure a server instance for [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)]**  
  
-   [Enable and Disable Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Enable-and-Disable-Always-On-Availability-Groups--SQL-Server-.md)  
  
-   [Create a Database Mirroring Endpoint for Always On Availability Groups (SQL Server PowerShell)](../../Topics/TopicNameContainA/Create-a-Database-Mirroring-Endpoint-for-Always-On-Availability-Groups--SQL-Server-PowerShell-.md)  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Mirroring-Endpoint-for-Windows-Authentication--Transact-SQL-.md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md)  
  
 **To get started with configuring Always On Availability Groups**  
  
-   [Getting Started with Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Getting-Started-with-Always-On-Availability-Groups--SQL-Server-.md)  
  
 **To create and configure a new availability group**  
  
-   [Use the Availability Group Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Availability-Group-Wizard--SQL-Server-Management-Studio-.md)  
  
-   [Create an Availability Group (Transact-SQL)](../../Topics/TopicNameNotContainA/Create-an-Availability-Group--Transact-SQL-.md)  
  
-   [Create an Availability Group (SQL Server PowerShell)](../../Topics/TopicNameNotContainA/Create-an-Availability-Group--SQL-Server-PowerShell-.md)  
  
-   [Use the New Availability Group Dialog Box (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-New-Availability-Group-Dialog-Box--SQL-Server-Management-Studio-.md)  
  
-   [Specify the Endpoint URL When Adding or Modifying an Availability Replica (SQL Server)](../../Topics/TopicNameNotContainA/Specify-the-Endpoint-URL-When-Adding-or-Modifying-an-Availability-Replica--SQL-Server-.md)  
  
-   [Create or Configure an Availability Group Listener (SQL Server)](../../Topics/TopicNameNotContainA/Create-or-Configure-an-Availability-Group-Listener--SQL-Server-.md)  
  
-   [Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (Always On Availability Groups)](../../Topics/TopicNameNotContainA/Configure-the-Flexible-Failover-Policy-to-Control-Conditions-for-Automatic-Failover--Always-On-Availability-Groups-.md)  
  
-   [Configure Backup on Availability Replicas (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Backup-on-Availability-Replicas--SQL-Server-.md)  
  
-   [Configure Read-Only Access on an Availability Replica (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Read-Only-Access-on-an-Availability-Replica--SQL-Server-.md)  
  
-   [Configure Read-Only Routing for an Availability Group (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Read-Only-Routing-for-an-Availability-Group--SQL-Server-.md)  
  
-   [Join a Secondary Replica to an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Join-a-Secondary-Replica-to-an-Availability-Group--SQL-Server-.md)  
  
-   [Start Data Movement on an Always On Secondary Database (SQL Server)](../../Topics/TopicNameNotContainA/Start-Data-Movement-on-an-Always-On-Secondary-Database--SQL-Server-.md)  
  
-   [Manually Prepare a Secondary Database for an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Manually-Prepare-a-Secondary-Database-for-an-Availability-Group--SQL-Server-.md)  
  
-   [Join a Secondary Database to an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Join-a-Secondary-Database-to-an-Availability-Group--SQL-Server-.md)  
  
-   [Management of Logins and Jobs for the Databases of an Availability Group (SQL Server)](../../Topics/TopicNameNotContainA/Management-of-Logins-and-Jobs-for-the-Databases-of-an-Availability-Group--SQL-Server-.md)  
  
 **To troubleshoot**  
  
-   [Troubleshoot Always On Availability Groups Configuration (SQL Server)](../../Topics/TopicNameNotContainA/Troubleshoot-Always-On-Availability-Groups-Configuration--SQL-Server-.md)  
  
-   [Troubleshoot a Failed Add-File Operation (Always On Availability Groups)](../../Topics/TopicNameContainA/Troubleshoot-a-Failed-Add-File-Operation--Always-On-Availability-Groups-.md)  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Blogs:**  
  
     [Always On - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server Always On Team Blogs: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server Engineers Blogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Videos:**  
  
     [Microsoft SQL Server Code-Named "Denali" Always On Series,Part 1: Introducing the Next Generation High Availability Solution](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Code-Named "Denali" Always On Series,Part 2: Building a Mission-Critical High Availability Solution Using Always On](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepapers:**  
  
     [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft White Papers for SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server Customer Advisory Team Whitepapers](http://sqlcat.com/)  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Administration of an Availability Group (SQL Server)](../../Topics/TopicNameNotContainA/Administration-of-an-Availability-Group--SQL-Server-.md)   
 [Always On Policies for Operational Issues with Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Always-On-Policies-for-Operational-Issues-with-Always-On-Availability-Groups--SQL-Server-.md)   
 [Monitoring of Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Monitoring-of-Availability-Groups--SQL-Server-.md)   
 [Always On Availability Groups: Interoperability (SQL Server)](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md)