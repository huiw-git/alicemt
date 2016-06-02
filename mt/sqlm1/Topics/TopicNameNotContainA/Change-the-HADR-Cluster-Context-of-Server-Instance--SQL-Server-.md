---
title: Change the HADR Cluster Context of Server Instance (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
---
# Change the HADR Cluster Context of Server Instance (SQL Server)
  This topic describes how to switch the HADR cluster context of an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] in [!INCLUDE[ssSQL11SP1](../../Token\Other/ssSQL11SP1_md.md)] and later versions. The *HADR cluster context* determines which Windows Server Failover Clustering \(WSFC\) cluster manages the metadata for availability replicas hosted by the server instance.  
  
 Switch the HADR cluster context only during a cross\-cluster migration of [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] to an instance of [!INCLUDE[ssSQL11SP1](../../Token\Other/ssSQL11SP1_md.md)] on a new WSFC cluster. Cross\-cluster migration of [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] supports OS upgrade to [!INCLUDE[win8](../../Token\Other/win8_md.md)] or [!INCLUDE[win8srv](../../Token\Other/win8srv_md.md)] with minimal downtime of availability groups. For more information, see [Cross\-Cluster Migration of Always On Availability Groups for OS Upgrade](http://msdn.microsoft.com/library/jj873730.aspx).  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Prerequisites](#Prerequisites)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To switch the cluster context of an availability replica, using:**  [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After Switching the Cluster Context of an Availability Replica](#FollowUp)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
> [!CAUTION]  
>  Switch the HADR cluster context only during cross\-cluster migration of [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] deployments.  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   You can switch the HADR cluster context only from the local WSFC cluster to a remote cluster and then back from the remote cluster to the local cluster. You cannot switch the HADR cluster context from one remote cluster to another remote cluster.  
  
-   The HADR cluster context can be switched to a remote cluster only when the instance of SQL Server is not hosting any availability replicas.  
  
-   A remote HADR cluster context can be switched back to the local cluster at any time. However, the context cannot be switched again as long as the server instance is hosting any availability replicas.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   The server instance on which you change the HADR cluster context must be running [!INCLUDE[ssSQL11SP1](../../Token\Other/ssSQL11SP1_md.md)] or above \(Enterprise edition or above\).  
  
-   The server instance must be enabled for Always On. For more information, see [Enable and Disable Always On Availability Groups &#40;SQL Server&#41;](../Topic/Enable%20and%20Disable%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
-   To be eligible to be switched from the local cluster context to a remote cluster cluster, a server instance cannot be hosting any availability replicas. The [sys.availability\_replicas](../Topic/sys.availability_replicas%20\(Transact-SQL\).md) catalog view should not return any rows.  
  
     If any availability replicas exist on the server instance, before you can change the HADR cluster context, you must do one of the following:  
  
    |Replica Role|Action|Link|  
    |------------------|------------|----------|  
    |Primary|Take the availability group offline.|[Take an Availability Group Offline &#40;SQL Server&#41;](../Topic/Take%20an%20Availability%20Group%20Offline%20\(SQL%20Server\).md)|  
    |Secondary|Remove the replica from its availability group|[Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Replica%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)|  
  
-   Before you can switch from a remote cluster to the local cluster, all synchronous\-commit replicas must be SYNCHRONIZED.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   We recommend that you specify the full domain name. This is because to find the target IP address of a short name, ALTER SERVER CONFIGURATION uses DNS resolution. Under some situations, depending on the DNS searching order, using a short name could cause confusion. For example, consider the following command, which is executed on a node in the `abc` domain, \(`node1.abc.com`\). The intended destination cluster is the `CLUS01` cluster in the `xyz` domain \(`clus01.xyz.com`\). However, the local  domain hosts also hosts a cluster named `CLUS01` \(`clus01.abc.com`\).  
  
     If the short name of the target cluster, `CLUS01`, were specified, DNS name resolution could return the IP address of the wrong cluster, `clus01.abc.com`. To avoid such confusion, specify the full name of the target cluster, as in the following example:  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
  
-   **SQL Server login**  
  
     Requires CONTROL SERVER permission.  
  
-   **SQL Server service account**  
  
     The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account of the server instance must have:  
  
    -   Permission to open the destination WSFC cluster.  
  
    -   Remote WSFC read\-write access.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To change the WSFC cluster context of an availability replica**  
  
1.  Connect to the server instance that hosts either the primary replica or a secondary replica of the availability group.  
  
2.  Use the SET HADR CLUSTER CONTEXT clause of the [ALTER SERVER CONFIGURATION](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **\=** { **'***windows\_cluster***'** | LOCAL }  
  
     where,  
  
     *windows\_cluster*  
     The cluster object name \(CON\) of a WSFC cluster. You can specify either the short name or the full domain name. We recommend that you specify the full domain name. For more information, see [Recommendations](#Recommendations), earlier in this topic.  
  
     LOCAL  
     The local WSFC cluster.  
  
### Examples  
 The following example changes the HADR cluster context to a different cluster. To identify the destination WSFC cluster, `clus01`, the example specifies the full cluster object name, `clus01.xyz.com`.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 The following example changes the HADR cluster context to the local WSFC cluster.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  
##  <a name="FollowUp"></a> Follow Up: After Switching the Cluster Context of an Availability Replica  
 The new HADR cluster context takes effect immediately, without restarting the server instance. The HADR cluster context setting is a persistent instance\-level setting that remains unchanged if the server instance restarts.  
  
 Confirm the new HADR cluster context by querying the [sys.dm\_hadr\_cluster](../Topic/sys.dm_hadr_cluster%20\(Transact-SQL\).md) dynamic management view, as follows:  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 This query should return the name of the cluster to which you set the HADR cluster context.  
  
 When the HADR cluster context is switched to a new cluster:  
  
-   The metadata is cleaned up for any availability replicas that are currently hosted by the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   All the databases that previously belonged to an availability replica are now in the RESTORING state.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Remove an Availability Group Listener &#40;SQL Server&#41;](../Topic/Remove%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
-   [Take an Availability Group Offline &#40;SQL Server&#41;](../Topic/Take%20an%20Availability%20Group%20Offline%20\(SQL%20Server\).md)  
  
-   [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Replica%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
-   [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [SQL Server 2012 Technical Articles](http://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [SQL Server Always On Team Blog: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
## See Also  
 [Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../Topic/Windows%20Server%20Failover%20Clustering%20\(WSFC\)%20with%20SQL%20Server.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md)  
  
  