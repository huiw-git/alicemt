---
title: Migrate SQL Server 2014 Managed Backup Settings to SQL Server 2016
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae937ebb-24ff-4a33-be3c-8f85328dfc75
---
# Migrate SQL Server 2014 Managed Backup Settings to SQL Server 2016
  This topic covers migration considerations for [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] when upgrading from [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] to [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
  
 The procedures and underlying behavior of [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] has changed in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. The following sections describe the functional changes and their implications.  
  
## Overview  
 The following table describes some of the key functional differences for [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] between [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] and [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
  
|Area|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]|[!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]|  
|----------|---------------------------|---------------------------|  
|**Namespace:**|smart\_admin|managed\_backup|  
|**System Stored Procedures:**|sp\_set\_db\_backup<br /><br /> sp\_set\_instance\_backup|[sp\_backup\_config\_basic](../Topic/managed_backup.sp_backup_config_basic%20\(Transact-SQL\).md)<br /><br /> [sp\_backup\_config\_advanced](../Topic/managed_backup.sp_backup_config_advanced%20\(Transact-SQL\).md)<br /><br /> [sp\_backup\_config\_schedule](../Topic/managed_backup.sp_backup_config_schedule%20\(Transact-SQL\).md)|  
|**Security:**|SQL credential using a Microsoft Azure storage account and access key.|SQL credential using a Microsoft Azure Shared Access Signature \(SAS\) token.|  
|**Underlying Storage:**|Microsoft Azure Storage using page blobs.|Microsoft Azure Storage using block blobs.|  
  
## Benefits  
 There are several benefits to using the new functionality in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
  
-   Block blobs cost less to store.  
  
-   With striping, you can store much larger backups \(12 TB versus 1 TB for page blobs\).  
  
-   Striping also improves the restore time for large databases  
  
-   For other improvements to [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], see [SQL Server Managed Backup to Microsoft Azure](../../Topics\TopicNameNotContainA/SQL-Server-Managed-Backup-to-Microsoft-Azure.md).  
  
## Considerations  
 After you upgrade from [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)], note the following [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] considerations:  
  
-   Any databases previously configured for [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] on [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] will continue to use the **smart\_admin** system procedures and underlying behavior on [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
  
-   The **smart\_admin** procedures are not supported for any new configurations of [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] on [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. You must use the new **managed\_backup** procedures and functionality.  
  
## See Also  
 [SQL Server Managed Backup to Microsoft Azure](../../Topics\TopicNameNotContainA/SQL-Server-Managed-Backup-to-Microsoft-Azure.md)  
  
  