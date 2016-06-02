---
title: Active Secondaries: Backup on Secondary Replicas (Always On Availability Groups)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
---
# Active Secondaries: Backup on Secondary Replicas (Always On Availability Groups)
  The [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] active secondary capabilities include support for performing backup operations on secondary replicas. Backup operations can put significant strain on I\/O and CPU \(with backup compression\). Offloading backups to a synchronized or synchronizing secondary replica allows you to use the resources on server instance that hosts the primary replica for your tier\-1 workloads.  
  
> [!NOTE]  
>  RESTORE statements are not allowed on either the primary or secondary databases of an availability group.  
  
-   [Supported Backup Types](#SupportedBuTypes)  
  
-   [Configuring Where Backup Jobs Run](#WhereBuJobsRun)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="SupportedBuTypes"></a> Backup Types Supported on Secondary Replicas  
  
-   **BACKUP DATABASE** supports only copy\-only full backups of databases, files, or filegroups when it is executed on secondary replicas. Note that copy\-only backups do not impact the log chain or clear the differential bitmap.  
  
-   Differential backups are not supported on secondary replicas.  
  
-   **BACKUP LOG** supports only regular log backups \(the COPY\_ONLY option is not supported for log backups on secondary replicas\).  
  
     A consistent log chain is ensured across log backups taken on any of the replicas \(primary or secondary\), irrespective of their availability mode \(synchronous\-commit or asynchronous\-commit\).  
  
-   To back up a secondary database, a secondary replica must be able to communicate with the primary replica and must be **SYNCHRONIZED** or **SYNCHRONIZING**.  
  
##  <a name="WhereBuJobsRun"></a> Configuring Where Backup Jobs Run  
 Performing backups on a secondary replica to offload the backup workload from the primary production server is a great benefit. However, performing backups on secondary replicas introduce significant complexity to the process of determining where backup jobs should run. To address this, configure where backup jobs run as follows:  
  
1.  Configure the availability group to specify which availability replicas where you would prefer backups to be performed. For more information, see *AUTOMATED\_BACKUP\_PREFERENCE* and *BACKUP\_PRIORITY* parameters in [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) or [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md).  
  
2.  Create scripted backup jobs for every availability database on every server instance that hosts an availability replica that is a candidate for performing backups. For more information, see the "Follow Up: After Configuring Backup on Secondary Replicas" section of [Configure Backup on Availability Replicas &#40;SQL Server&#41;](../Topic/Configure%20Backup%20on%20Availability%20Replicas%20\(SQL%20Server\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To configure backup on secondary replicas**  
  
-   [Configure Backup on Availability Replicas &#40;SQL Server&#41;](../Topic/Configure%20Backup%20on%20Availability%20Replicas%20\(SQL%20Server\).md)  
  
 **To determine whether the current replica is the preferred backup replica**  
  
-   [sys.fn\_hadr\_backup\_is\_preferred\_replica](../Topic/sys.fn_hadr_backup_is_preferred_replica%20%20\(Transact-SQL\).md)  
  
 **To create a backup job**  
  
-   [Use the Maintenance Plan Wizard](../../Topics\TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md)  
  
-   [Implement Jobs](../Topic/Implement%20Jobs.md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Copy-Only Backups &#40;SQL Server&#41;](../Topic/Copy-Only%20Backups%20\(SQL%20Server\).md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)  
  
  