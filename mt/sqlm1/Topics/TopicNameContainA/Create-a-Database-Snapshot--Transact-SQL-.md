---
title: Create a Database Snapshot (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
---
# Create a Database Snapshot (Transact-SQL)
  The only way to create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database snapshot is to use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] does not support the creation of database snapshots.  
  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
 The source database, which can use any recovery model, must meet the following prerequisites:  
  
-   The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that supports database snapshot. For information about support for database snapshots in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
-   The source database must be online, unless the database is a mirror database within a database mirroring session.  
  
-   To create a database snapshot on a mirror database, the database must be in the synchronized [mirroring state](../Topic/Mirroring%20States%20\(SQL%20Server\).md).  
  
-   The source database cannot be configured as a scalable shared database.  

>  **Important!** For information about other significant considerations, see [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md).  
  
##  <a name="Recommendations"></a> Recommendations  
 This section discusses the following best practices:  
  
-   [Best Practice: Naming Database Snapshots](#Naming)  
  
-   [Best Practice: Limiting the Number of Database Snapshots](#Limiting_Number)  
  
-   [Best Practice: Client Connections to a Database Snapshot](#Client_Connections)  
  
####  <a name="Naming"></a> Best Practice: Naming Database Snapshots  
 Before creating snapshots, it is important to consider how to name them. Each database snapshot requires a unique database name. For administrative ease, the name of a snapshot can incorporate information that identifies the database, such as:  
  
-   The name of the source database.  
  
-   An indication that the new name is for a snapshot.  
  
-   The creation date and time of the snapshot, a sequence number, or some other information, such as time of day, to distinguish sequential snapshots on a given database.  
  
 For example, consider a series of snapshots for the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database. Three daily snapshots are created at 6\-hour intervals between 6 A.M. and 6 P.M., based on a 24\-hour clock. Each daily snapshot is kept for 24 hours before being dropped and replaced by a new snapshot of the same name. Note that each snapshot name indicates the hour, but not the day:  
  
```  
AdventureWorks_snapshot_0600  
AdventureWorks_snapshot_1200  
AdventureWorks_snapshot_1800  
```  
  
 Alternatively, if the creation time of these daily snapshots varies from day to day, a less precise naming convention might be preferable, for example:  
  
```  
AdventureWorks_snapshot_morning  
AdventureWorks_snapshot_noon  
AdventureWorks_snapshot_evening  
```  
  
#### <a name="Limiting_Number"></a> Best Practice: Limiting the Number of Database Snapshots  
 Creating a series of snapshots over time captures sequential snapshots of the source database. Each snapshot persists until it is explicitly dropped. Because each snapshot will continue to grow as original pages are updated, you may want to conserve disk space by deleting an older snapshot after creating a new snapshot.  
  

**Note!** To revert to a database snapshot, you need to delete any other snapshots from that database.  
  
####  <a name="Client_Connections"></a> Best Practice: Client Connections to a Database Snapshot  
 To use a database snapshot, clients need to know where to find it. Users can read from one database snapshot while another is being created or deleted. However, when you substitute a new snapshot for an existing one, you need to redirect clients to the new snapshot. Users can manually connect to a database snapshot by means of [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. However, to support a production environment, you should create a programmatic solution that transparently directs report\-writing clients to the latest database snapshot of the database.  
  

  
####  <a name="Permissions"></a> Permissions  
 Any user who can create a database can create a database snapshot; however, to create a snapshot of a mirror database, you must be a member of the **sysadmin** fixed server role.  
  
##  <a name="TsqlProcedure"></a> How to Create a Database Snapshot \(Using Transact\-SQL\)  
 **To create a database snapshot**  
  
>  For an example of this procedure, see [Examples \(Transact\-SQL\)](#TsqlExample), later in this section.  
  
1.  Based on the current size of the source database, ensure that you have sufficient disk space to hold the database snapshot. The maximum size of a database snapshot is the size of the source database at snapshot creation. For more information, see [View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;](../Topic/View%20the%20Size%20of%20the%20Sparse%20File%20of%20a%20Database%20Snapshot%20\(Transact-SQL\).md).  
  
2.  Issue a CREATE DATABASE statement on the files using the AS SNAPSHOT OF clause. Creating a snapshot requires specifying the logical name of every database file of the source database. The syntax is as follows:  
  
     CREATE DATABASE *database\_snapshot\_name*  
  
     ON  
  
     \(  
  
     NAME \=*logical\_file\_name*,  
  
     FILENAME \='*os\_file\_name*'  
  
     \) \[ ,...*n* \]  
  
     AS SNAPSHOT OF *source\_database\_name*  
  
     \[;\]  
  
     Where *source\_**database\_name* is the source database, *logical\_file\_name i*s the logical name used in SQL Server when referencing the file, *os\_file\_name* is the path and file name used by the operating system when you create the file, and *database\_snapshot\_name* is the name of the snapshot to which you want to revert the database. For a full description of this syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20\(SQL%20Server%20Transact-SQL\).md).  
  
    > [!NOTE]  
    >  When you create a database snapshot, log files, offline files, restoring files, and defunct files are not allowed in the CREATE DATABASE statement.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
  
> [!NOTE]  
>  The `.ss` extension used in the examples is arbitrary.  
  
 This section contains the following examples:  
  
-   A. [Creating a snapshot on the AdventureWorks database](#Creating_on_AW)  
  
-   B. [Creating a snapshot on the Sales database](#Creating_on_Sales)  
  
####  <a name="Creating_on_AW"></a> A. Creating a snapshot on the AdventureWorks database  
 This example creates a database snapshot on the `AdventureWorks` database. The snapshot name, `AdventureWorks_dbss_1800`, and the file name of its sparse file, `AdventureWorks_data_1800.ss`, indicate the creation time, 6 P.M \(1800 hours\).  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks_Data, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="Creating_on_Sales"></a> B. Creating a snapshot on the Sales database  
 This example creates a database snapshot, `sales_snapshot1200`, on the `Sales` database. This database was created in the example, "Creating a database that has filegroups," in [CREATE DATABASE (SQL Server Transact-SQL)](../Topic/CREATE%20DATABASE%20\(SQL%20Server%20Transact-SQL\).md).  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [View a Database Snapshot &#40;SQL Server&#41;](../Topic/View%20a%20Database%20Snapshot%20\(SQL%20Server\).md)  
  
-   [Revert a Database to a Database Snapshot](../../Topics\TopicNameContainA/Revert-a-Database-to-a-Database-Snapshot.md)  
  
-   [Drop a Database Snapshot &#40;Transact-SQL&#41;](../Topic/Drop%20a%20Database%20Snapshot%20\(Transact-SQL\).md)  
  
## See Also  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20\(SQL%20Server%20Transact-SQL\).md)   
 [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md)  
  
  