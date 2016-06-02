---
title: Configure Backup Compression (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
---
# Configure Backup Compression (SQL Server)
  At installation, backup compression is off by default. The default behavior for backup compression is defined by the **backup compression default** Option server\-level configuration option. However, you can override the server\-level default when creating a single backup or scheduling a series of routine backups. To change the server\-level default, see [View or Configure the backup compression default Server Configuration Option](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md).  
  
## Override the Backup Compression Default  
 You can change the backup compression behavior for an individual backup, backup job, or log shipping configuration.  
  
-   **[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]**  
  
     To override the server backup\-compression default when creating a backup, use either WITH NO\_COMPRESSION or WITH COMPRESSION in you [BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) statement.  
  
     For a log shipping configuration, you can control the backup compression behavior of log backups by using [sp\_add\_log\_shipping\_primary\_database](../Topic/sp_add_log_shipping_primary_database%20\(Transact-SQL\).md)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](../Topic/sp_change_log_shipping_primary_database%20\(Transact-SQL\).md).  
  
-   **[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]**  
  
     For information about how to view or configure the backup compression default option for an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [View or Configure the backup compression default Server Configuration Option](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md).  
  
     You can override the server backup\-compression default when creating a backup by specifying **Compress backup** or **Do not compress backup** in any of the following dialog boxes:  
  
    -   [Back Up Database \(Options Page\)](../Topic/Back%20Up%20Database%20\(Backup%20Options%20Page\).md)  
  
         When backing up a database, you can control backup compression for an individual database, file, or log backup.  
  
    -   [Use the Maintenance Plan Wizard](../../Topics\TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md)  
  
         The Maintenance Plan Wizard enables you to control backup compression for each set full or differential database backups or log backups that you schedule.  
  
    -   Integration Services \(SSIS\) [Back Up Database task](../../Topics\TopicNameNotContainA/Back-Up-Database-Task.md)  
  
         You can control the backup compression behavior when creating a package for backing up a single database or multiple databases.  
  
    -   [Log Shipping Transaction Log Backup Settings](../../Topics\TopicNameNotContainA/Log-Shipping-Transaction-Log-Backup-Settings.md)  
  
         You can control the backup compression behavior of log backups.  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Backup Compression &#40;SQL Server&#41;](../Topic/Backup%20Compression%20\(SQL%20Server\).md)  
  
  