---
title: Take an Availability Group Offline (SQL Server)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
---
# Take an Availability Group Offline (SQL Server)
  This topic describes how to take an Always On availability group from the ONLINE state to the OFFLINE state by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] in [!INCLUDE[ssSQL11SP1](../../Topics/TopicNameNotContainA/includes/ssSQL11SP1_md.md)] and later versions. There is no data loss for synchronous-commit databases because if any synchronous-commit replica is not synchronized, the OFFLINE operation raises an error and leaves the availability group ONLINE. Keeping the availability group online protects unsynchronized synchronous-commit databases from possible data loss. After an availability group goes offline, its databases become unavailable to clients and you cannot bring the availability group back online. Therefore, take an availability group offline only to migrate the availability group resources from one WSFC cluster to another.  
  
 During a cross-cluster migration of [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)], if any applications connect directly to the primary replica of an availability group, the availability group must be taken offline. Cross-cluster migration of [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] supports OS upgrade with minimal downtime of availability groups. The typical scenario is to use cross-cluster migration of [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/includes/ssHADR_md.md)] for OS upgrade to [!INCLUDE[win8](../../Topics/TopicNameContainA/includes/win8_md.md)] or [!INCLUDE[win8srv](../../Topics/TopicNameContainA/includes/win8srv_md.md)]. For more information, see [Cross-Cluster Migration of Always On Availability Groups for OS Upgrade](http://msdn.microsoft.com/library/jj873730.aspx).  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To take an availability group offline, using:**  [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After the Availability Group Goes Offline](#FollowUp)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
> [!CAUTION]  
>  Use the OFFLINE option only for a cross-cluster migration of availability group resources.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   The server instance on which you enter the OFFLINE command must be running [!INCLUDE[ssSQL11SP1](../../Topics/TopicNameNotContainA/includes/ssSQL11SP1_md.md)] or above (Enterprise edition or above).  
  
-   The availability group must currently be online.  
  
###  <a name="Recommendations"></a> Recommendations  
 Before you take the availability group offline, delete the availability group listener or listeners. For more information, see [Remove an Availability Group Listener &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Remove-an-Availability-Group-Listener--SQL-Server-.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 **To take an availability group offline**  
  
1.  Connect to a server instance that hosts an availability replica for the availability group. This replica can be the primary replica or a secondary replica.  
  
2.  Use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER AVAILABILITY GROUP *group_name* OFFLINE  
  
     where *group_name* is the name of the availability group.  
  
### Example  
 The following example takes the `AccountsAG` availability group offline.  
  
```  
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="FollowUp"></a> Follow Up: After the Availability Group Goes Offline  
  
-   **Logging of OFFLINE operation:**  The identity of the WSFC node where the OFFLINE operation was initiated is stored in both the WSFC cluster log and the SQL ERRORLOG.  
  
-   **If you did not delete the availability group listener before taking the group offline:**  If you are migrating the availability group to another WSFC cluster, delete the VNN and VIP of the listener. You can delete them by using either the Failover Cluster Management console, the [Remove-ClusterResource](http://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell cmdlet, or [cluster.exe](http://technet.microsoft.com/library/ee461015\(WS.10\).aspx). Note that cluster.exe is deprecated on Windows 8.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Remove an Availability Group Listener &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Remove-an-Availability-Group-Listener--SQL-Server-.md)  
  
-   [Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Change-the-HADR-Cluster-Context-of-Server-Instance--SQL-Server-.md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [SQL Server 2012 Technical Articles](http://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [SQL Server Always On Team Blog: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
## See Also  
 [Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Always-On-Availability-Groups--SQL-Server-.md)  
  
  