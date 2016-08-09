---
title: "Active Secondaries: Backup on Secondary Replicas (Always On Availability Groups)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# Active Secondaries: Backup on Secondary Replicas (Always On Availability Groups)
The [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] active secondary capabilities include support for performing backup operations on secondary replicas. Backup operations can put significant strain on I/O and CPU (with backup compression). Offloading backups to a synchronized or synchronizing secondary replica allows you to use the resources on server instance that hosts the primary replica for your tier-1 workloads.  
  
> [!NOTE]  
>  RESTORE statements are not allowed on either the primary or secondary databases of an availability group.  
  
-   [Supported Backup Types](#SupportedBuTypes)  
  
-   [Configuring Where Backup Jobs Run](#WhereBuJobsRun)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="SupportedBuTypes"></a> Backup Types Supported on Secondary Replicas  
  
-   **BACKUP DATABASE** supports only copy-only full backups of databases, files, or filegroups when it is executed on secondary replicas. Note that copy-only backups do not impact the log chain or clear the differential bitmap.  
  
-   Differential backups are not supported on secondary replicas.  
  
-   **BACKUP LOG** supports only regular log backups (the COPY_ONLY option is not supported for log backups on secondary replicas).  
  
     A consistent log chain is ensured across log backups taken on any of the replicas (primary or secondary), irrespective of their availability mode (synchronous-commit or asynchronous-commit).  
  
-   To back up a secondary database, a secondary replica must be able to communicate with the primary replica and must be **SYNCHRONIZED** or **SYNCHRONIZING**.  
  
##  <a name="WhereBuJobsRun"></a> Configuring Where Backup Jobs Run  
 Performing backups on a secondary replica to offload the backup workload from the primary production server is a great benefit. However, performing backups on secondary replicas introduce significant complexity to the process of determining where backup jobs should run. To address this, configure where backup jobs run as follows:  
  
1.  Configure the availability group to specify which availability replicas where you would prefer backups to be performed. For more information, see *AUTOMATED_BACKUP_PREFERENCE* and *BACKUP_PRIORITY* parameters in [CREATE AVAILABILTY GROUP](assetId:///a3d55df7-b4e4-43f3-a14b-056cba36ab98) or [ALTER AVAILABILITY GROUP](assetId:///f039d0de-ade7-4aaf-8b7b-d207deb3371a).  
  
2.  Create scripted backup jobs for every availability database on every server instance that hosts an availability replica that is a candidate for performing backups. For more information, see the "Follow Up: After Configuring Backup on Secondary Replicas" section of [Configure Backup on Availability Replicas (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Backup-on-Availability-Replicas--SQL-Server-.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To configure backup on secondary replicas**  
  
-   [Configure Backup on Availability Replicas (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Backup-on-Availability-Replicas--SQL-Server-.md)  
  
 **To determine whether the current replica is the preferred backup replica**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](assetId:///61b9be77-e2f6-4da1-b2ae-a62cbe226145)  
  
 **To create a backup job**  
  
-   [Use the Maintenance Plan Wizard](../../Topics/TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md)  
  
-   [Implement Jobs](assetId:///69e06724-25c7-4fb3-8a5b-3d4596f21756)  
  
   
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Copy-Only Backups (SQL Server)](../../Topics/TopicNameNotContainA/Copy-Only-Backups--SQL-Server-.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](assetId:///a3d55df7-b4e4-43f3-a14b-056cba36ab98)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](assetId:///f039d0de-ade7-4aaf-8b7b-d207deb3371a)