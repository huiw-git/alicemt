---
title: Monitoring of Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
---
# Monitoring of Availability Groups (SQL Server)
  To monitor the properties and state of an Always On availability group you can use the following tools.  
  
|Tool|Brief Description|Links|  
|----------|-----------------------|-----------|  
|System Center Monitoring pack for SQL Server|The Monitoring pack for SQL Server \(SQLMP\) is the recommended solution for monitoring availability groups, availability replica and availability databases for IT administrators. Monitoring features that are particularly relevance to [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] include the following:<br /><br /> Automatic discoverability of availability groups, availability replicas, and availability database from among hundreds of computers. This enables you to easily keep track of your [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] inventory.<br /><br /> Fully capable System Center Operations Manager \(SCOM\) alerting and ticketing. These features provide detailed knowledge that enables faster resolution to a problem.<br /><br /> A custom extension to Always On Health monitoring using Policy Based management \(PBM\).<br /><br /> Health roll ups from availability databases to availability replicas.<br /><br /> Custom tasks that manage [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] from the System Center Operations Manager console.|To download the monitoring pack \(SQLServerMP.msi\) and *SQL Server Management Pack Guide for System Center Operations Manager* \(SQLServerMPGuide.doc\), see:<br /><br /> [System Center Monitoring pack for SQL Server](http://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]|[!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] catalog and dynamic management views provide a wealth of information about your availability groups and their replicas, databases, listeners, and WSFC cluster environment.|[Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)|  
|[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]|The **Object Explorer Details** pane displays basic information about the availability groups hosted on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to which you are connected.<br /><br /> **\*\* Tip \*\*** Use this pane to select multiple availability groups, replicas, or databases and to perform routine administrative tasks on the selected objects; for example, removing multiple availability replicas or databases from an availability group.|[Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Object%20Explorer%20Details%20to%20Monitor%20Availability%20Groups%20\(SQL%20Server%20Management%20Studio\).md)|  
|[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]|**Properties** dialog boxes enable you to view the properties of availability groups, replicas, or listeners and, in some cases, to change their values.|-   [View Availability Group Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Properties%20\(SQL%20Server\).md)<br />-   [View Availability Replica Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Replica%20Properties%20\(SQL%20Server\).md)<br />-   [View Availability Group Listener Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Listener%20Properties%20\(SQL%20Server\).md)|  
|System Monitor|The **SQLServer:Availability Replica** performance object contains performance counters that report information about availability replicas.|[SQL Server, Availability Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Availability-Replica.md)|  
|System Monitor|The **SQLServer:Database Replica** performance object contains performance counters that report information about the secondary databases on a given secondary replica.<br /><br /> The **SQLServer:Databases** object in SQL Server contains performance counters that monitor transaction log activities, among other things. The following counters are particularly relevant for monitoring transaction\-log activity on availability databases: **Log Flush Write Time \(ms\)**, **Log Flushes\/sec**, **Log Pool Cache Misses\/sec**, **Log Pool Disk Reads\/sec**, and **Log Pool Requests\/sec**.|[SQL Server, Database Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Database-Replica.md) and [SQL Server, Databases Object](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md)|  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Blogs:**  
  
     [The Always On Health Model Part 1 \-\- Health Model Architecture](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/09/overview-of-the-Always%20On-manageability-health-model.aspx)  
  
     [The Always On Health Model Part 2 \-\- Extending the Health Model](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/extending-the-Always%20On-health-model.aspx)  
  
     [Monitoring Always On Health with PowerShell \- Part 1: Basic Cmdlet Overview](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/monitoring-Always%20On-health-with-powershell-part-1.aspx)  
  
     [Monitoring Always On Health with PowerShell \- Part 2: Advanced Cmdlet Usage](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/monitoring-Always%20On-health-with-powershell-part-2.aspx)  
  
     [Monitoring Always On Health with PowerShell \- Part 3 : A Simple Monitoring Application](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/15/monitoring-Always%20On-health-with-powershell-part-3.aspx)  
  
     [Monitoring Always On Health with PowerShell \- Part 4 : Integration with SQL Server Agent](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
     [SQL Server Always On Team Blogs: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server Engineers Blogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Whitepapers:**  
  
     [Microsoft White Papers for SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server Customer Advisory Team Whitepapers](http://sqlcat.com/)  
  
## See Also  
 [Always On Availability Groups Catalog Views &#40;Transact-SQL&#41;](../Topic/Always%20On%20Availability%20Groups%20Catalog%20Views%20\(Transact-SQL\).md)   
 [Always On Availability Groups Dynamic Management Views and Functions &#40;Transact-SQL&#41;](../Topic/Always%20On%20Availability%20Groups%20Dynamic%20Management%20Views%20and%20Functions%20\(Transact-SQL\).md)   
 [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](../Topic/Flexible%20Failover%20Policy%20for%20Automatic%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Automatic Page Repair &#40;Availability Groups: Database Mirroring&#41;](../Topic/Automatic%20Page%20Repair%20\(Availability%20Groups:%20Database%20Mirroring\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  