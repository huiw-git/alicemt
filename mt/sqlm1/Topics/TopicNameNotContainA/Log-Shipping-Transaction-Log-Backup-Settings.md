---
title: Log Shipping Transaction Log Backup Settings
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a6e6c16-7f71-412b-bba6-7bffac001277
---
# Log Shipping Transaction Log Backup Settings
  Use this dialog box to configure and modify the transaction log backup settings for a log shipping configuration.  
  
 For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../Topic/About%20Log%20Shipping%20\(SQL%20Server\).md).  
  
## Options  
 **Network path to the backup folder**  
 Type the network share to your backup folder in this box. The local folder where your transaction log backups are saved must be shared so that the log shipping copy jobs can copy these files to the secondary server. You must grant read permissions on this network share to the proxy account under which the copy job will run at the secondary server instance. By default, this is the SQLServerAgent service account of the secondary server instance, but an administrator can choose another proxy account for the job.  
  
 **If the backup folder is located on the primary server, type the local path to the folder**  
 Type the local drive letter and path to the backup folder if the backup folder is located on the primary server. If the backup folder is not located on the primary server, you can leave this blank.  
  
 If you specify a local path here, the BACKUP command will use this path to create the transaction log backups; otherwise, if no local path is specified, the BACKUP command will use the network path specified in the **Network path to the backup folder** box.  
  
> [!NOTE]  
>  If the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account is running under the local system account on the primary server, you must create the backup folder on the primary server and specify the local path to that folder here. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account of the primary server instance must have Read and Write permissions on this folder.  
  
 **Delete files older than**  
 Specify the length of time you want transaction log backups to remain in your backup directory before being deleted.  
  
 **Alert if no backup occurs within**  
 Specify the amount of time you want log shipping to wait before raising an alert that no transaction log backups have occurred.  
  
 **Job name**  
 Displays the name of the SQL Server Agent job that is used to create the transaction log backups for log shipping. When first creating the job, you can modify the name by typing in the box.  
  
 **Schedule**  
 Displays the current schedule for backing up the transaction logs of the primary database. Before the backup job has been created, You can modify this schedule by clicking **Schedule...**. After the job has been created, you can modify this schedule by clicking **Edit Job...**.  
  
### Backup Job  
 **Schedule...**  
 Modify the schedule that is created when the SQL Server Agent job is created.  
  
 **Edit Job...**  
 Modify the SQL Server Agent job parameters for the job that performs transaction log backups on the primary database.  
  
 **Disable this job**  
 Disable the SQL Server Agent job from creating transaction log backups.  
  
### Compression  
 [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)] \(or a later version\) supports [backup compression](../Topic/Backup%20Compression%20\(SQL%20Server\).md).  
  
 **Set backup compression**  
 In [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)] \(or a later version\), select one the following backup compression values for the log backups of this log shipping configuration:  
  
|||  
|-|-|  
|**Use the default server setting**|Click to use the server\-level default.<br /><br /> This default is set by the **backup compression default** server\-configuration option. For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md).|  
|**Compress backup**|Click to compress the backup, regardless of the server\-level default.<br /><br /> **\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations. Therefore, you might want to create low\-priority compressed backups in a session whose CPU usage is limited by the [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md). For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../Topic/Use%20Resource%20Governor%20to%20Limit%20CPU%20Usage%20by%20Backup%20Compression%20\(Transact-SQL\).md).|  
|**Do not compress backup**|Click to create an uncompressed backup, regardless of the server\-level default.|  
  
## See Also  
 [Configure a User to Create and Manage SQL Server Agent Jobs](../Topic/Configure%20a%20User%20to%20Create%20and%20Manage%20SQL%20Server%20Agent%20Jobs.md)   
 [About Log Shipping &#40;SQL Server&#41;](../Topic/About%20Log%20Shipping%20\(SQL%20Server\).md)  
  
  