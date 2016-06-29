---
title: Back Up Database (Backup Options Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df0ddcdb-c94e-472b-b786-469ae8117b93
---
# Back Up Database (Backup Options Page)
  Use the  **Backup Options** page of the **Back Up Database** dialog box to view or modify database backup options.  
  
 **To create a backup by using SQL Server Management Studio**  
  
-   [Create a Full Database Backup &#40;SQL Server&#41;](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md)  
  
-   [Create a Differential Database Backup &#40;SQL Server&#41;](../../Topics/TopicNameContainA/Create-a-Differential-Database-Backup--SQL-Server-.md)  
  
> [!IMPORTANT]  
>  You can define a database maintenance plan to create database backups. For more information, see [Maintenance Plans](../../Topics/TopicNameNotContainA/Maintenance-Plans.md) and [Use the Maintenance Plan Wizard](../../Topics/TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md).  
  
> [!NOTE]  
>  When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/includes/ssManStudioFull_md.md)], you can generate the corresponding [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)][BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) script by clicking the **Script** button and then selecting a destination for the script.  
  
## Options  
  
### Backup set  
 The options of the **Backup set** panel allow for you to specify optional information about the backup set created by the back up operation.  
  
 **Name**  
 Specify the backup set name. The system automatically suggests a default name based on the database name and the backup type.  
  
 For information about backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md).  
  
 **Description**  
 Enter a description of the backup set.  
  
 **Backup set will expire**  
 Choose one of the following expiration options. This option is disabled if **URL** is chosen as the backup destination.  
  
|||  
|-|-|  
|**After**|Specify the number of days that must elapse before this backup set expires and can be overwritten. This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.<br /><br /> The default value for backup expiration is the value set in the **Default backup media retention (in days)** option. To access this, right-click the server name in Object Explorer and select **Properties**; then click the **Database Settings** page of the **Server Properties** dialog box.|  
|**On**|Specify a specific date when the backup set expires and can be overwritten.|  
  
### Compression  
 [!INCLUDE[ssEnterpriseEd10](../../Topics/TopicNameContainA/includes/ssEnterpriseEd10_md.md)] (or a later version) supports [backup compression](../../Topics/TopicNameNotContainA/Backup-Compression--SQL-Server-.md).  
  
 **Set backup compression**  
 In [!INCLUDE[ssEnterpriseEd10](../../Topics/TopicNameContainA/includes/ssEnterpriseEd10_md.md)] (or a later version), select one of the following backup compression values:  
  
|||  
|-|-|  
|**Use the default server setting**|Click to use the server-level default.<br /><br /> This default is set by the **backup compression default** server-configuration option. For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../Topics/TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md).|  
|**Compress backup**|Click to compress the backup, regardless of the server-level default.<br /><br /> **\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations. Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md). For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../Topics/TopicNameNotContainA/Use-Resource-Governor-to-Limit-CPU-Usage-by-Backup-Compression--Transact-SQL-.md).|  
|**Do not compress backup**|Click to create an uncompressed backup, regardless of the server-level default.|  
  
### Encryption  
 To create an encrypted backup, check the **Encrypt backup** check box. Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys. The available algorithms for encryption are:  
  
-   AES 128  
  
-   AES 192  
  
-   AES 256  
  
-   Triple DES  
  
> [!TIP]  
>  The encryption option is disabled if you selected to append to existing backup set.  
>   
>  It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.  
>   
>  Only keys residing in the Extensible Key Management (EKM) are supported.  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [Back Up a Transaction Log &#40;SQL Server&#41;](../../Topics/TopicNameContainA/Back-Up-a-Transaction-Log--SQL-Server-.md)   
 [Back Up Files and Filegroups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Back-Up-Files-and-Filegroups--SQL-Server-.md)   
 [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Back-Up-the-Transaction-Log-When-the-Database-Is-Damaged--SQL-Server-.md)  
  
  