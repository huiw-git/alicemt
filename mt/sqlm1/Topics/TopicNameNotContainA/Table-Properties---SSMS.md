---
title: Table Properties - SSMS
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
---
# Table Properties - SSMS
  This topic describes the table properties that are displayed in the Table Properties dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For more information about how to display these properties, see [View the Table Definition](../../Topics\TopicNameNotContainA/View-the-Table-Definition.md).  
  
 **In This Topic**  
  
1.  [General Page](#GeneralPage)  
  
2.  [Change Tracking Page](#ChangeTracking)  
  
3.  [File Table Page](#FileTable)  
  
4.  [Storage Page](#Storage)  
  
##  <a name="GeneralPage"></a> General Page  
 **Database**  
 The name of the database containing this table.  
  
 **Server**  
 The name of the current server instance.  
  
 **User**  
 The name of the user of this connection.  
  
 **Created Date**  
 The date and time that the table was created.  
  
 **Name**  
 The name of the table.  
  
 **Schema**  
 The schema that owns the table.  
  
 **System object**  
 Indicates this table is a system table, used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to contain internal information. Users should not directly change or reference system tables.  
  
 **ANSI NULLs**  
 Indicates if the object was created with the ANSI NULLs option set to ON. For more information, see [SET ANSI_NULLS &#40;Transact-SQL&#41;](../Topic/SET%20ANSI_NULLS%20\(Transact-SQL\).md)  
  
 **Quoted identifier**  
 Indicates if the object was created with the quoted identifier option set to ON. For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../Topic/SET%20QUOTED_IDENTIFIER%20\(Transact-SQL\).md)  
  
 **Lock Escalation**  
 Indicates the lock escalation granularity of the table. For more information about locking in the Database Engine, see [SQL Server Transaction Locking and Row Versioning Guide](http://msdn.microsoft.com/library/jj856598.aspx). Possible values are:  
  
 AUTO  
 This option allows the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] to select the lock escalation granularity that is appropriate for the table schema.  
  
-   If the table is partitioned, lock escalation will be allowed to the heap or B\-tree \(HoBT\) granularity. After the lock is escalated to the HoBT level, the lock will not be escalated later to TABLE granularity.  
  
-   If the table is not partitioned, the lock escalation will be done to the TABLE granularity.  
  
 TABLE  
 Lock escalation will be done at table\-level granularity regardless of whether the table is partitioned or not partitioned. TABLE is the default value.  
  
 DISABLE  
 Prevents lock escalation in most cases. Table\-level locks are not completely disallowed. For example, when you are scanning a table that has no clustered index under the serializable isolation level, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] must take a table lock to protect data integrity.  
  
 **Table is replicated**  
 Indicates when the table is replicated to another database using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication. Possible values are **True** or **False**.  
  
##  <a name="ChangeTracking"></a> Change Tracking Page  
 **Change Tracking**  
 Indicates whether change tracking is enabled for the table. The default value is **False**.  
  
 This option is available only when change tracking is enabled for the database.  
  
 To enable change tracking, the table must have a primary key, and you must have permission to modify the table. You can configure change tracking by using [ALTER TABLE](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md).  
  
 **Track Columns Updated**  
 Indicates whether the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] tracks which columns were updated.  
  
 For more information about Change Tracking, see [About Change Tracking &#40;SQL Server&#41;](../Topic/About%20Change%20Tracking%20\(SQL%20Server\).md).  
  
##  <a name="FileTable"></a> FileTable Page  
 Displays properties of the table related to FileTables. For more information, see [FileTables &#40;SQL Server&#41;](../Topic/FileTables%20\(SQL%20Server\).md).  
  
 **FileTable name column collation**  
 The collation that is applied to the **Name** column in a FileTable. The **Name** column contains file and directory names.  
  
 **FileTable directory name**  
 The root folder for the FileTable.  
  
 **FileTable namespace enabled**  
 When **True**, this value indicates that the table is a FileTable. If you change this value to **False**, you are changing the FileTable to an ordinary user table. If you later want to change the table back to a FileTable, the table will have to pass a FileTable consistency check before the conversion succeeds.  
  
##  <a name="Storage"></a> Storage Page  
 Displays the storage related properties of the selected table.  
  
### Compression  
 **Compression type**  
 The compression type of the table. This property is only available for tables that are not partitioned. For more information, see [Data Compression](../../Topics\TopicNameNotContainA/Data-Compression.md).  
  
 **Partitions using page compression**  
 The partition numbers that are using page compression. This property is only available for partitioned tables.  
  
 **Partitions not compressed**  
 The partition numbers that are not compressed. This property is only available for partitioned tables.  
  
 **Partitions using row compression**  
 The partition numbers that are using row compression. This property is only available for partitioned tables.  
  
### Filegroup  
 **Text filegroup**  
 The name of the filegroup that contains the text data for the table.  
  
 **Filegroup**  
 The name of the filegroup that contains the table.  
  
 **Table is partitioned**  
 Possible values are **True** and **False**.  
  
 **Filestream filegroup**  
 Specify the name of the FILESTREAM data filegroup if the table has a **varbinary\(max\)** column that has the FILESTREAM attribute. The default value is the default FILESTREAM data filegroup.  
  
 If the table does not contain FILESTREAM data, the field is blank.  
  
### General  
 **Vardecimal storage format is enabled**  
 When **True**, this read\-only value indicates that **decimal** and **numeric** data types are stored by using the vardecimal storage format. To change this option, use the **vardecimal storage format** option of [sp\_tableoption](../Topic/sp_tableoption%20\(Transact-SQL\).md). Vardecimal storage format is deprecated. Use ROW compression instead.  
  
 **Index space**  
 The amount of space in megabytes that the indexes occupy in the table. This value does not include XML index space usage for the table. If XML indexes belong to the table, use [sp\_spaceused](../Topic/sp_spaceused%20\(Transact-SQL\).md) instead.  
  
 **Row count**  
 The number of rows in the table.  
  
 **Data space**  
 The amount of space in megabytes that the data occupies in the table.  
  
### Partitioning  
 This section is only available if the table is partitioned. For more information, see [Partitioned Tables and Indexes](../../Topics\TopicNameNotContainA/Partitioned-Tables-and-Indexes.md).  
  
 **Partition column**  
 The name of the column on which the table is partitioned.  
  
 **Partition scheme**  
 Name of the partition scheme if the table is partitioned. If the table is not partitioned, the field is blank.  
  
 **Number of partitions**  
 The number of partitions in the table.  
  
 **FILESTREAM partition scheme**  
 The name of the FILESTREAM partition scheme if the table is partitioned. If the table is not partitioned, the field is blank.  
  
 The FILESTREAM partition scheme must be symmetric to the scheme that is specified in the **Partition scheme** option.  
  
## See Also  
 [View the Table Definition](../../Topics\TopicNameNotContainA/View-the-Table-Definition.md)   
 [Modify Columns &#40;Database Engine&#41;](../Topic/Modify%20Columns%20\(Database%20Engine\).md)  
  
  