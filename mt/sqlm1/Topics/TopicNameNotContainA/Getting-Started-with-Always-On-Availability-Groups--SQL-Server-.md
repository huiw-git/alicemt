---
title: Getting Started with Always On Availability Groups (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 33f2f2d0-79e0-4107-9902-d67019b826aa
---
# Getting Started with Always On Availability Groups (SQL Server)
    This topic introduces the steps for configuring instances of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] to support [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] and for creating, managing, and monitoring an availability group.  
  
-   **Before You Begin:**  
  
     [Recommended Reading](#RecommendedReading)  
  
-   **Getting started with:**  
  
     [Configuring an instance of SQL Server to support Always On Availability Groups](#ConfigSI)  
  
     [Creating and configuring a new availability group](#ConfigAG)  
  
     [Managing availability groups, replicas, and databases](#ManageAGsEtc)  
  
     [Monitoring availability groups](#MonitorAGsEtc)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="RecommendedReading"></a> Recommended Reading  
 Before you create your first availability group, we recommend that you read the following topics:  
  
-   [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
-   [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
##  <a name="ConfigSI"></a> Configuring an Instance of SQL Server to Support Always On Availability Groups  
  
||Step|Links|  
|------|----------|-----------|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Enable [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)].** The [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] feature must be enabled on every instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that is to participate in an availability group.<br /><br /> **Prerequisites:**  The host computer must be a Windows Server Failover Clustering \(WSFC\) node.<br /><br /> For information about the other prerequisites, see "SQL Server Instance Prerequisites and Restrictions" in [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).|[Enable and disable Always On Availability Groups](../Topic/Enable%20and%20Disable%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Create database mirroring endpoint \(if none\).** Ensure that each server instance possesses a [database mirroring endpoint](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md). The server instance uses this endpoint to receive [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] connections from other server instances.|To determine whether database mirroring endpoint exists: <br />                    [sys.database\_mirroring\_endpoints](../Topic/sys.database_mirroring_endpoints%20\(Transact-SQL\).md)<br /><br /> **For Windows Authentication**.  To create a database mirroring endpoint, using:<br /><br /> [New Availability Group Wizard](../Topic/Use%20the%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)<br /><br /> [Transact\-SQL](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)<br /><br /> [SQL Server PowerShell](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server%20PowerShell\).md)<br /><br /> **For certificate authentication**. To create a database mirroring endpoint, using:[Transact\-SQL](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md)|  
  
##  <a name="ConfigAG"></a> Creating and Configuring a New Availability Group  
  
||Step|Links|  
|------|----------|-----------|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Create the availability group.** Create the availability group on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that hosts the databases to be added to the availability group.<br /><br /> Minimally, create the initial primary replica on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] where you create the availability group. You can specify from one to four secondary replicas. For information about availability group and replica properties, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md).<br /><br /> We strongly recommend that you create an [availability group listener](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md).<br /><br /> **Prerequisites:**  The instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that host availability replicas for a given availability group must reside on separate nodes of a single WSFC cluster. The only exception is that while being migrated to another WSFC cluster, an availability group can temporarily straddle two clusters.<br /><br /> For information about the other prerequisites, see "Availability Group Prerequisites and Restrictions", "Availability Database Prerequisites and Restrictions", and "SQL Server Instance Prerequisites and Restrictions" in [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).|To create an availability group you can use any of the following tools:<br /><br /> [New Availability Group Wizard](../Topic/Use%20the%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)<br /><br /> [Transact\-SQL](../Topic/Create%20an%20Availability%20Group%20\(Transact-SQL\).md)<br /><br /> [SQL Server PowerShell](../Topic/Create%20an%20Availability%20Group%20\(Transact-SQL\).md)|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Join secondary replicas to the availability group.** Connect to each instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that is hosting a secondary replica, and join the local secondary replica to the availability group.|[Join a secondary replica to an availability group](../Topic/Join%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> Tip: If you use the New Availability Group Wizard, this step is automated.|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Prepare secondary databases.** On every server instance that is hosting a secondary replica, restore backups of the primary databases using RESTORE WITH NORECOVERY.|[Manually prepare a secondary database](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> Tip: The New Availability Group Wizard can prepare the secondary databases for you. For more information, see "Prerequisites for using full initial data synchronization" in [Select Initial Data Synchronization Page &#40;Always On Availability Group Wizards&#41;](../Topic/Select%20Initial%20Data%20Synchronization%20Page%20\(Always%20On%20Availability%20Group%20Wizards\).md).|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Join secondary databases to the availability group.** On every server instance that is hosting a secondary replica, join each local secondary database to the availability group. On joining the availability group, a given secondary database initiates data synchronization with the corresponding primary database.|[Join a secondary database to an availability group](../Topic/Join%20a%20Secondary%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> Tip: The New Availability Group Wizard can perform this step if every secondary database exists on every secondary replica.|  
||**Create an availability group listener.**  This step is necessary unless you already created the availability group listener while creating the availability group.|[Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Give the listener's DNS host name to application developers.**  Developers needs to specify this DNS name in the connection strings to direct connection requests to the availability group listener. For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md).|"Follow Up: After Creating an Availability Group Listener" in [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)|  
|![Checkbox](../../Images\Image\ImageNotContaina/CheckboxEmptyCenterXtraSpaceTopAndRight.gif "CheckboxEmptyCenterXtraSpaceTopAndRight")|**Configure Where Backup Jobs.**  If you want to perform backups on secondary databases, you must create a backup job script that takes the automated backup preference into account. Create a script for each database in the availability group on every server instance that hosts an availability replica for the availability group.|"Follow Up: After Configuring Backup on Secondary Replicas" in [Configure Backup on Availability Replicas &#40;SQL Server&#41;](../Topic/Configure%20Backup%20on%20Availability%20Replicas%20\(SQL%20Server\).md)|  
  
##  <a name="ManageAGsEtc"></a> Managing Availability Groups, Replicas, and Databases  
  
> [!NOTE]  
>  For information about availability group and replica properties, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md).  
  
 Managing existing availability groups involves one or more of the following tasks:  
  
|Task|Link|  
|----------|----------|  
|Modify the [flexible failover policy](../Topic/Flexible%20Failover%20Policy%20for%20Automatic%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md) of the availability group to control the conditions that cause an automatic failover. This policy is relevant only when automatic failover is possible.|[Configure the flexible failover policy of an availability group](../Topic/Configure%20the%20Flexible%20Failover%20Policy%20to%20Control%20Conditions%20for%20Automatic%20Failover%20\(Always%20On%20Availability%20Groups\).md)|  
|Perform a planned manual failover or a forced manual failover \(with possible data loss\), typically called *forced failover*. For more information, see [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../Topic/Failover%20and%20Failover%20Modes%20\(Always%20On%20Availability%20Groups\).md).|[Perform a planned manual failover](../Topic/Perform%20a%20Planned%20Manual%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> [Perform a forced manual failover](../Topic/Perform%20a%20Forced%20Manual%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)|  
|Use a set of predefined policies to view the health of an availability group and its replicas and databases.|[Use policy\-based management to view the health of availability groups](../Topic/Use%20Always%20On%20Policies%20to%20View%20the%20Health%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> [Use the Always On Group Dashboard](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)|  
|Add or remove a secondary replica.|[Add a secondary replica](../Topic/Add%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> [Remove a secondary replica](../Topic/Remove%20a%20Secondary%20Replica%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)|  
|Suspend or resume an availability database. Suspending a secondary database keeps at its current point in time until you resume it.|[Suspend a database](../Topic/Suspend%20an%20Availability%20Database%20\(SQL%20Server\).md)<br /><br /> [Resume a database](../Topic/Resume%20an%20Availability%20Database%20\(SQL%20Server\).md)|  
|Add or remove a database.|[Add a database](../Topic/Add%20a%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> [Remove a secondary database](../Topic/Remove%20a%20Secondary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> [Remove a primary database](../Topic/Remove%20a%20Primary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)|  
|Reconfigure or create an availability group listener.|[Create or configure an availability group listener](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)|  
|Delete an availability group.|[Delete an availability group](../Topic/Remove%20an%20Availability%20Group%20\(SQL%20Server\).md)|  
|Troubleshoot add file operations. This might be required if the primary database and a secondary database have different file paths.|[Troubleshoot a failed add\-file operation](../Topic/Troubleshoot%20a%20Failed%20Add-File%20Operation%20\(Always%20On%20Availability%20Groups\).md)|  
|Alter availability replica properties.|[Change the Availability Mode](../Topic/Change%20the%20Availability%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md)<br /><br /> [Change the Failover Mode](../Topic/Change%20the%20Failover%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md)<br /><br /> [Configure Backup Priority \(and Automated Backup Preference\)](../Topic/Configure%20Backup%20on%20Availability%20Replicas%20\(SQL%20Server\).md)<br /><br /> [Configure Read\-Only Access](../Topic/Configure%20Read-Only%20Access%20on%20an%20Availability%20Replica%20\(SQL%20Server\).md)<br /><br /> [Configure Read\-Only Routing](../Topic/Configure%20Read-Only%20Routing%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)<br /><br /> [Change the Session\-Timeout Period](../Topic/Change%20the%20Session-Timeout%20Period%20for%20an%20Availability%20Replica%20\(SQL%20Server\).md)|  
  
##  <a name="MonitorAGsEtc"></a> Monitoring Availability Groups  
 To monitor the properties and state of an Always On availability group you can use the following tools.  
  
|Tool|Brief Description|Links|  
|----------|-----------------------|-----------|  
|System Center Monitoring pack for SQL Server|The Monitoring pack for SQL Server \(SQLMP\) is the recommended solution for monitoring availability groups, availability replica and availability databases for IT administrators. Monitoring features that are particularly relevance to [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] include the following:<br /><br /> Automatic discoverability of availability groups, availability replicas, and availability database from among hundreds of computers. This enables you to easily keep track of your [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] inventory.<br /><br /> Fully capable System Center Operations Manager \(SCOM\) alerting and ticketing. These features provide detailed knowledge that enables faster resolution to a problem.<br /><br /> A custom extension to Always On Health monitoring using Policy Based management \(PBM\).<br /><br /> Health roll ups from availability databases to availability replicas.<br /><br /> Custom tasks that manage [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] from the System Center Operations Manager console.|To download the monitoring pack \(SQLServerMP.msi\) and *SQL Server Management Pack Guide for System Center Operations Manager* \(SQLServerMPGuide.doc\), see:<br /><br /> [System Center Monitoring pack for SQL Server](http://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]|[!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] catalog and dynamic management views provide a wealth of information about your availability groups and their replicas, databases, listeners, and WSFC cluster environment.|[Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)|  
|[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]|The **Object Explorer Details** pane displays basic information about the availability groups hosted on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to which you are connected.<br /><br /> Tip: Use this pane to select multiple availability groups, replicas, or databases and to perform routine administrative tasks on the selected objects; for example, removing multiple availability replicas or databases from an availability group.|[Use Object Explorer Details to monitor availability groups](../Topic/Use%20the%20Object%20Explorer%20Details%20to%20Monitor%20Availability%20Groups%20\(SQL%20Server%20Management%20Studio\).md)|  
|[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]|**Properties** dialog boxes enable you to view the properties of availability groups, replicas, or listeners and, in some cases, to change their values.|[Availability Group Properties](../Topic/View%20Availability%20Group%20Properties%20\(SQL%20Server\).md)<br /><br /> [Availability Replica Properties](../Topic/View%20Availability%20Replica%20Properties%20\(SQL%20Server\).md)<br /><br /> [Availability Group Listener Properties](../Topic/View%20Availability%20Group%20Listener%20Properties%20\(SQL%20Server\).md)|  
|System Monitor|The **SQLServer:Availability Replica** performance object contains performance counters that report information about availability replicas.|[SQL Server, Availability Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Availability-Replica.md)|  
|System Monitor|The **SQLServer:Database Replica** performance object contains performance counters that report information about the secondary databases on a given secondary replica.<br /><br /> The **SQLServer:Databases** object in SQL Server contains performance counters that monitor transaction log activities, among other things. The following counters are particularly relevant for monitoring transaction\-log activity on availability databases: **Log Flush Write Time \(ms\)**, **Log Flushes\/sec**, **Log Pool Cache Misses\/sec**, **Log Pool Disk Reads\/sec**, and **Log Pool Requests\/sec**.|[SQL Server, Database Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Database-Replica.md)<br /><br /> [SQL Server, Databases Object](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md)|  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Video—Introduction to Always On:**  [Microsoft SQL Server Code\-Named "Denali" Always On Series,Part 1: Introducing the Next Generation High Availability Solution](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
-   **Video—A Deep Dive into Always On:**  [Microsoft SQL Server Code\-Named "Denali" Always On Series,Part 2: Building a Mission\-Critical High Availability Solution Using Always On](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepaper:**  [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   **Blogs:**  [SQL Server Always On Team Blog: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
## See Also  
 [Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Configuration of a Server Instance for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Configuration%20of%20a%20Server%20Instance%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../Topic/Creation%20and%20Configuration%20of%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Monitoring of Availability Groups &#40;SQL Server&#41;](../Topic/Monitoring%20of%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Overview of Transact-SQL Statements for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Transact-SQL%20Statements%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Overview of PowerShell Cmdlets for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20PowerShell%20Cmdlets%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  