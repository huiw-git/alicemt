---
title: Flexible Failover Policy for Automatic Failover of an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c504c7f-5c1d-4124-b697-f735ef0084f0
---
# Flexible Failover Policy for Automatic Failover of an Availability Group (SQL Server)
  A flexible failover policy provides granular control over the conditions that cause [automatic failover](../Topic/Failover%20and%20Failover%20Modes%20\(Always%20On%20Availability%20Groups\).md) for an availability group. By changing the failure conditions that trigger an automatic failover and the frequency of health checks, you can increase or decrease the likelihood of an automatic failover to support your SLA for high availability.  
  
 The flexible failover policy of an availability group is defined by its failure\-condition level and health\-check timeout threshold. On detecting that an availability group has exceeded its failure condition level or its health\-check timeout threshold, the availability group's resource DLL responds back to the Windows Server Failover Clustering \(WSFC\) cluster. The WSFC cluster then initiates an automatic failover to the secondary replica.  
  
> [!IMPORTANT]  
>  If an availability group exceeds its WSFC failure threshold, the WSFC cluster will not attempt an automatic failover for the availability group. Furthermore, the WSFC resource group of the availability group remains in a failed state until either the cluster administrator manually brings the failed resource group online or the database administrator performs a manual failover of the availability group. The *WSFC failure threshold* is defined as the maximum number of failures supported for the availability group during a given time period. The default time period is six hours, and the default value for the maximum number of failures during this period is *n*\-1, where *n* is the number of WSFC nodes. To change the failure\-threshold values for a given availability group, use the WSFC Failover Manager Console.  
  
 This topic contains the following sections:  
  
-   [Health\-Check Timeout Threshold](#HCtimeout)  
  
-   [Failure\-Condition Level](#FClevel)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="HCtimeout"></a> Health\-Check Timeout Threshold  
 WSFC resource DLL of the availability group performs a *health check* of the primary replica by calling the [sp\_server\_diagnostics](../Topic/sp_server_diagnostics%20\(Transact-SQL\).md) stored procedure on the instance of SQL Server that hosts the primary replica. **sp\_server\_diagnostics** returns results at an interval that equals 1\/3 of the health\-check timeout threshold for the availability group. The default health\-check timeout threshold is 30 seconds, which causes **sp\_server\_diagnostics** to return at a 10\-second interval. If **sp\_server\_diagnostics** is slow or is not returning information, the resource DLL will wait for the full interval of the health\-check timeout threshold before determining that the primary replica is unresponsive. If the primary replica is unresponsive, an automatic failover is initiated, if currently supported.  
  
> [!IMPORTANT]  
>  **sp\_server\_diagnostics** does not perform health checks at the database level.  
  
##  <a name="FClevel"></a> Failure\-Condition Level  
 Whether the diagnostic data and health information returned by **sp\_server\_diagnostics** warrants an automatic failover depends on the failure\-condition level of the availability group. The *failure\-condition level* specifies what failure conditions trigger an automatic failover. There are five failure\-condition levels, which range from the least restrictive \(level one\) to the most restrictive \(level five\). A given level encompasses the less restrictive levels. Thus, the strictest level, five, includes the four less restrictive conditions, and so forth.  
  
> [!IMPORTANT]  
>  Damaged databases and suspect databases are not detected by any failure\-condition level. Therefore, a database that is damaged or suspect \(whether due to a hardware failure, data corruption, or other issue\) never triggers an automatic failover.  
  
 The following table describes the failure\-conditions that corresponds to each level.  
  
|Level|Failure Condition|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] Value|PowerShell Value|  
|-----------|-----------------------|------------------------------|----------------------|  
|One|On server down. Specifies that an automatic failover is initiated when one the following occurs:<br /><br /> The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service is down.<br /><br /> The lease of the availability group for connecting to the WSFC cluster expires because no ACK is received from the server instance. For more information, see [How It Works: SQL Server Always On Lease Timeout](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx).<br /><br /> <br /><br /> This is the least restrictive level.|1|**OnServerDown**|  
|Two|On server unresponsive. Specifies that an automatic failover is initiated when one of the following occurs:<br /><br /> The instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not connect to cluster, and the user\-specified health check timeout threshold of the availability group is exceeded.<br /><br /> The availability replica is in failed state.|2|**OnServerUnresponsive**|  
|Three|On critical server error. Specifies that an automatic failover is initiated on critical [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] internal errors, such as orphaned spinlocks, serious write\-access violations, or too much dumping.<br /><br /> This is the default level.|3|**OnCriticalServerError**|  
|Four|On moderate server error. Specifies that an automatic failover is initiated on moderate [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] internal errors, such as a persistent out\-of\-memory condition in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] internal resource pool.|4|**OnModerateServerError**|  
|Five|On any qualified failure conditions. Specifies that an automatic failover is initiated on any qualified failure conditions, including:<br /><br /> Exhaustion of SQL Engine worker\-threads.<br /><br /> Detection of an unsolvable deadlock.<br /><br /> <br /><br /> This is the most restrictive level.|5|**OnAnyQualifiedFailureConditions**|  
  
> [!NOTE]  
>  Lack of response by an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to client requests is irrelevant to availability groups.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To configure automatic failover**  
  
-   [Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Availability%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md) \(automatic failover requires synchronous\-commit availability mode\)  
  
-   [Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Failover%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Configure the Flexible Failover Policy to Control Conditions for Automatic Failover &#40;Always On Availability Groups&#41;](../Topic/Configure%20the%20Flexible%20Failover%20Policy%20to%20Control%20Conditions%20for%20Automatic%20Failover%20\(Always%20On%20Availability%20Groups\).md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [How It Works: SQL Server Always On Lease Timeout](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Availability Modes &#40;Always On Availability Groups&#41;](../Topic/Availability%20Modes%20\(Always%20On%20Availability%20Groups\).md)   
 [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../Topic/Failover%20and%20Failover%20Modes%20\(Always%20On%20Availability%20Groups\).md)   
 [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../Topic/Windows%20Server%20Failover%20Clustering%20\(WSFC\)%20with%20SQL%20Server.md)   
 [Failover Policy for Failover Cluster Instances](../../Topics\TopicNameNotContainA/Failover-Policy-for-Failover-Cluster-Instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](../Topic/sp_server_diagnostics%20\(Transact-SQL\).md)  
  
  