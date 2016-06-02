---
title: Restore a Database Backup Under the Simple Recovery Model (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
---
# Restore a Database Backup Under the Simple Recovery Model (Transact-SQL)
  This topic explains how to restore a full database backup.  
  
> [!IMPORTANT]  
>  The system administrator restoring the full database backup must be the only person currently using the database to be restored.  
  
## Prerequisites and Recommendations  
  
-   To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database. Without the certificate or asymmetric key, the database cannot be restored. As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed. For more information, see [SQL Server Certificates and Asymmetric Keys](../../Topics\TopicNameNotContainA/SQL-Server-Certificates-and-Asymmetric-Keys.md).  
  
-   For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources. Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] code or cause errors by modifying the schema or the physical database structure. Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](../Topic/DBCC%20CHECKDB%20\(Transact-SQL\).md) on the database on a nonproduction server and also examine the code, such as stored procedures or other user\-defined code, in the database.  
  
## Database Compatibility Level After Upgrade  
 The compatibility levels of the **tempdb**, **model**, **msdb** and **Resource** databases are set to the compatibility level of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] after upgrade. The **master** system database retains the compatibility level it had before upgrade, unless that level was less than 100. If the compatibility level of **master** was less than 100 before upgrade, it is set to 100 after upgrade.  
  
 If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade. If the compatibility level was 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
> [!NOTE]  
>  New user databases will inherit the compatibility level of the **model** database.  
  
## Procedures  
  
#### To restore a full database backup  
  
1.  Execute the RESTORE DATABASE statement to restore the full database backup, specifying:  
  
    -   The name of the database to restore.  
  
    -   The backup device from where the full database backup is restored.  
  
    -   The NORECOVERY clause if you have a transaction log or differential database backup to apply after restoring the full database backup.  
  
    > [!IMPORTANT]  
    >  To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database. Without the certificate or asymmetric key, the database cannot be restored. As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed. For more information, see [SQL Server Certificates and Asymmetric Keys](../../Topics\TopicNameNotContainA/SQL-Server-Certificates-and-Asymmetric-Keys.md).  
  
2.  Optionally, specify:  
  
    -   The FILE clause to identify the backup set on the backup device to restore.  
  
> [!NOTE]  
>  If you restore an earlier version database to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], the database is automatically upgraded. Typically, the database becomes available immediately. However, if a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] database has full\-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade\_option** server property. If the upgrade option is set to import \(**upgrade\_option** \= 2\) or rebuild \(**upgrade\_option** \= 0\), the full\-text indexes will be unavailable during the upgrade. Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer. Note also that when the upgrade option is set to import, the associated full\-text indexes are rebuilt if a full\-text catalog is not available. To change the setting of the **upgrade\_option** server property, use [sp\_fulltext\_service](../Topic/sp_fulltext_service%20\(Transact-SQL\).md).  
  
## Example  
  
### Description  
 This example restores the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] full database backup from tape.  
  
### Example  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## See Also  
 [Complete Database Restores &#40;Full Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Full%20Recovery%20Model\).md)   
 [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Full Database Backups &#40;SQL Server&#41;](../Topic/Full%20Database%20Backups%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Backup History and Header Information &#40;SQL Server&#41;](../Topic/Backup%20History%20and%20Header%20Information%20\(SQL%20Server\).md)   
 [Rebuild System Databases](../../Topics\TopicNameNotContainA/Rebuild-System-Databases.md)  
  
  