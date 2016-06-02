---
title: Back Up and Restore Full-Text Catalogs and Indexes
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
---
# Back Up and Restore Full-Text Catalogs and Indexes
  This topic explains how to back up and restore full\-text indexes created in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the full\-text catalog is a logical concept and does not reside in a filegroup. Therefore, to back up a full\-text catalog in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you must identify every filegroup that contains a full\-text index that belongs to the catalog. Then you must back up those filegroups, one by one.  
  
> [!IMPORTANT]  
>  It is possible to import full\-text catalogs when upgrading a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] database. Each imported full\-text catalog is a database file in its own filegroup. To back up an imported catalog, simply back up its filegroup. For more information, see [Backing Up and Restoring Full\-Text Catalogs](http://go.microsoft.com/fwlink/?LinkID=121052), in [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] Books Online.  
  
##  <a name="backingup"></a> Backing Up the Full\-Text Indexes of a Full\-Text Catalog  
  
###  <a name="Find_FTIs_of_a_Catalog"></a> Finding the Full\-Text Indexes of a Full\-Text Catalog  
 You can retrieve the properties of the full\-text indexes by using the following [SELECT](../Topic/SELECT%20\(Transact-SQL\).md) statement, which selects columns from the [sys.fulltext\_indexes](../Topic/sys.fulltext_indexes%20\(Transact-SQL\).md) and [sys.fulltext\_catalogs](../Topic/sys.fulltext_catalogs%20\(Transact-SQL\).md) catalog views.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  
 [In This Topic](#top)  
  
###  <a name="Find_FG_of_FTI"></a> Finding the Filegroup or File That Contains a Full\-Text Index  
 When a full\-text index is created, it is placed in one of the following locations:  
  
-   A user\-specified filegroup.  
  
-   The same filegroup as base table or view, for a nonpartitioned table.  
  
-   The primary filegroup, for a partitioned table.  
  
> [!NOTE]  
>  For information about creating a full\-text index, see [Create and Manage Full-Text Indexes](../../Topics\TopicNameNotContainA/Create-and-Manage-Full-Text-Indexes.md) and [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../Topic/CREATE%20FULLTEXT%20INDEX%20\(Transact-SQL\).md).  
  
 To find the filegroup of full\-text index on a table or view, use the following query, where *object\_name* is the name of the table or view:  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  
 [In This Topic](#top)  
  
###  <a name="Back_up_FTIs_of_FTC"></a> Backing Up the Filegroups That Contain Full\-Text Indexes  
 After you find the filegroups that contain the indexes of a full\-text catalog, you need back up each of the filegroups. During the backup process, full\-text catalogs may not be dropped or added.  
  
 The first backup of a filegroup must be a full file backup. After you have created a full file backup for a filegroup, you could back up only the changes in a filegroup by creating a series of one or more differential file backups that are based on the full file backup.  
  
 **To back up files and filegroups**  
  
-   [Back Up Files and Filegroups &#40;SQL Server&#41;](../Topic/Back%20Up%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)  
  
 [In This Topic](#top)  
  
##  <a name="Restore_FTI"></a> Restoring a Full\-Text Index  
 Restoring a backed\-up filegroup restores the full\-text index files, as well as the other files in the filegroup. By default, the filegroup is restored to the disk location on which the filegroup was backed up.  
  
 If a full\-text indexed table was online and a population was running when the backup was created, the population is resumed after the restore.  
  
 **To restore a filegroup**  
  
-   [Restore Files and Filegroups &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20over%20Existing%20Files%20\(SQL%20Server\).md)  
  
-   [Restore Files to a New Location &#40;SQL Server&#41;](../Topic/Restore%20Files%20to%20a%20New%20Location%20\(SQL%20Server\).md)  
  
-   [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
 [In This Topic](#top)  
  
## See Also  
 [Manage and Monitor Full-Text Search for a Server Instance](../../Topics\TopicNameContainA/Manage-and-Monitor-Full-Text-Search-for-a-Server-Instance.md)   
 [Upgrade Full-Text Search](../../Topics\TopicNameNotContainA/Upgrade-Full-Text-Search.md)  
  
  