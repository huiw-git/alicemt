---
title: Backup Compression (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05bc9c4f-3947-4dd4-b823-db77519bd4d2
---
# Backup Compression (SQL Server)
  This topic describes the compression of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backups, including restrictions, performance trade\-off of compressing backups, the configuration of backup compression, and the compression ratio.  
  
> [!NOTE]  
>  For information regarding which editions of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] support backup compression, see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md). Every edition of [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] and later can restore a compressed backup.  
  
  
##  <a name="Benefits"></a> Benefits  
  
-   Because a compressed backup is smaller than an uncompressed backup of the same data, compressing a backup typically requires less device I\/O and therefore usually increases backup speed significantly.  
  
     For more information, see [Performance Impact of Compressing Backups](#PerfImpact), later in this topic.  
  
  
##  <a name="Restrictions"></a> Restrictions  
 The following restrictions apply to compressed backups:  
  
-   Compressed and uncompressed backups cannot co\-exist in a media set.  
  
-   Previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot read compressed backups.  
  
-   NTbackups cannot share a tape with compressed [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backups.  
  
  
##  <a name="PerfImpact"></a> Performance Impact of Compressing Backups  
 By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations. Therefore, you might want to create low\-priority compressed backups in a session whose CPU usage is limited by[Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md). For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../Topic/Use%20Resource%20Governor%20to%20Limit%20CPU%20Usage%20by%20Backup%20Compression%20\(Transact-SQL\).md).  
  
 To obtain a good picture of your backup I\/O performance, you can isolate the backup I\/O to or from devices by evaluating the following sorts of performance counters:  
  
-   Windows I\/O performance counters, such as the physical\-disk counters  
  
-   The **Device Throughput Bytes\/sec** counter of the [SQLServer:Backup Device](../../Topics\TopicNameNotContainA/SQL-Server,-Backup-Device-Object.md) object  
  
-   The **Backup\/Restore Throughput\/sec** counter of the [SQLServer:Databases](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md) object  
  
 For information about Windows counters, see Windows help. For information about how to work with SQL Server counters, see [Use SQL Server Objects](../../Topics\TopicNameNotContainA/Use-SQL-Server-Objects.md).  
  
   
##  <a name="CompressionRatio"></a> Calculate the Compression Ratio of a Compressed Backup  
 To calculate the compression ratio of a backup, use the values for the backup in the **backup\_size** and **compressed\_backup\_size** columns of the [backupset](../Topic/backupset%20\(Transact-SQL\).md) history table, as follows:  
  
 **backup\_size**:**compressed\_backup\_size**  
  
 For example, a 3:1 compression ratio indicates that you are saving about 66% on disk space. To query on these columns, you can use the following Transact\-SQL statement:  
  
```  
SELECT backup_size/compressed_backup_size FROM msdb..backupset;  
```  
  
 The compression ratio of a compressed backup depends on the data that has been compressed. A variety of factors can impact the compression ratio obtained. Major factors include:  
  
-   The type of data.  
  
     Character data compresses more than other types of data.  
  
-   The consistency of the data among rows on a page.  
  
     Typically, if a page contains several rows in which a field contains the same value, significant compression might occur for that value. In contrast, for a database that contains random data or that contains only one large row per page, a compressed backup would be almost as large as an uncompressed backup.  
  
-   Whether the data is encrypted.  
  
     Encrypted data compresses significantly less than equivalent unencrypted data. If transparent data encryption is used to encrypt an entire database, compressing backups might not reduce their size by much, if at all.  
  
-   Whether the database is compressed.  
  
     If the database is compressed, compressing backups might not reduce their size by much, if at all.  
  
  
##  <a name="Allocation"></a> Allocation of Space for the Backup File  
 For compressed backups, the size of the final backup file depends on how compressible the data is, and this is unknown before the backup operation finishes.  Therefore, by default, when backing up a database using compression, the Database Engine uses a pre\-allocation algorithm for the backup file. This algorithm pre\-allocates a predefined percentage of the size of the database for the backup file. If more space is needed during the backup operation, the Database Engine grows the file. If the final size is less than the allocated space, at the end of the backup operation, the Database Engine shrinks the file to the actual final size of the backup.  
  
 To allow the backup file to grow only as needed to reach its final size, use trace flag 3042. Trace flag 3042 causes the backup operation to bypass the default backup compression pre\-allocation algorithm. This trace flag is useful if you need to save on space by allocating only the actual size required for the compressed backup. However, using this trace flag might cause a slight performance penalty \(a possible increase in the duration of the backup operation\).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Configure Backup Compression &#40;SQL Server&#41;](../Topic/Configure%20Backup%20Compression%20\(SQL%20Server\).md)  
  
-   [View or Configure the backup compression default Server Configuration Option](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md)  
  
-   [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../Topic/Use%20Resource%20Governor%20to%20Limit%20CPU%20Usage%20by%20Backup%20Compression%20\(Transact-SQL\).md)  
  
-   [DBCC TRACEON &#40;Transact-SQL&#41;](../Topic/DBCC%20TRACEON%20\(Transact-SQL\).md)  
  
-   [DBCC TRACEOFF &#40;Transact-SQL&#41;](../Topic/DBCC%20TRACEOFF%20\(Transact-SQL\).md)  
  
## See Also  
 [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md)   
 [Trace Flags &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md)  
  
  