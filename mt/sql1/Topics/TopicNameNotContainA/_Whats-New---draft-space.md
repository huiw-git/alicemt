---
title: "_Whats New - draft space"
ms.custom: na
ms.date: 06/29/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6df6b7e6-df89-42cf-b71d-c9952cd35a0e
caps.latest.revision: 7
---
# _Whats New - draft space
Use this topic to draft content for next months SQL Server What's new topics. This topic will note be published, but you can draft content in advance and then copy / paste into the topics we publish live.  
  
## SQL Server Setup - new this month  
 For information on what's new with installation and information on previous months, see[Installation for SQL Server 2016](../../Topics/TopicNameNotContainA/Installation-for-SQL-Server-2016.md)  
  
## Analysis Services Engine (SSAS) - new this month  
 For more detailed what's new information and information on previous months, see [What's New in Analysis Services](../../Topics/TopicNameNotContainA/What-s-New-in-Analysis-Services.md).  
  
## Database Engine - new this month  
 For more detailed what's new information and information on previous months, see [What's New in Database Engine](../../Topics/TopicNameNotContainA/What-s-New-in-Database-Engine.md).  
  
## Integration Services (SSIS) - new this month  
 For more detailed what's new information and information on previous months, see [What's New in Integration Services](../../Topics/TopicNameNotContainA/What-s-New-in-Integration-Services.md).  
  
## Reporting Services (SSRS) - new this month  
 For more detailed what's new information and information on previous months, see [What's New in Reporting Services (SSRS)](../../Topics/TopicNameNotContainA/What-s-New-in-Reporting-Services--SSRS-.md).  
  
##  <a name="bkmk_ssrservices"></a> SQL Server R Services - new this month  
 For more detailed what's new information and information on previous months, see  [What's New in SQL Server R Services](../../Topics/TopicNameNotContainA/What-s-New-in-SQL-Server-R-Services.md).  
  
## !!! just to be safe !!  
 the following was all copied from the main whats new before I purged it for RC1, just in case something from rc0 was needed..  
  
 ![horizontal&#95;bar](../../Topics/TopicNameNotContainA/images/horizontal_bar.png "horizontal_bar")  
  
##  <a name="bkmk_dbengine"></a> Database Engine - new this month  
 **Support for UTF-8** – [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md), [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2), and [OPENROWSET](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17) now support the UTF-8 code page. For more information, see those topics and [Create a Format File (SQL Server)](../../Topics/TopicNameContainA/Create-a-Format-File--SQL-Server-.md).  
  
 **New string functions** – [STRING_SPLIT (Transact-SQL)](assetId:///3273dbf3-0b4f-41e1-b97e-b4f67ad370b9) and [STRING_ESCAPE (Transact-SQL)](assetId:///2163bc7a-3816-4304-9c40-8954804f5465) are added.  
  
 **New JSON_MODIFY function**. The built-in support for JSON also now includes the [JSON_MODIFY (Transact-SQL)](assetId:///96bc8255-a037-4907-aec4-1a9c30814651) function. Use the **JSON_MODIFY**  function to update the value of a property in a JSON string and return the updated JSON string.  
  
 **New or improved in Stretch Database**  
  
-   **New preview version on Azure**. A preview of a new version of Stretch Database on Azure that supports 60 TB of data is now available. To register for preview access, go to [SQL Server Stretch Database preview](https://azure.microsoft.com/en-us/services/sql-server-stretch-database/request/).  
  
-   **Azure Active Directory authentication**. The option to use a federated service account for SQL Server to communicate with the remote Azure SQL Database server when certain conditions are true no longer requires a trace flag. For more info, see [Enable Stretch Database for a database](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-database.md).  
  
 **Real-time operational analytics and columnstore indexes**  
  
-   **Compression delay.** This new option minimizes the impact of columnstore index on the transactional workload for real-time operational analytics.   To specify compression delay, use [CREATE TABLE (Transact-SQL)](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b) or [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1). You can specify compression delay both for disk-based and memory-optimized tables.  
  
-   **Group by performance enhancement.** A query with a GROUP BY clause is  eligible for aggregate pushdown when run against a nonclustered columnstore index. With this improvement, the scan operations are performed more efficiently. Previously this was available only for a clustered columnstore index.  
  
-   **New alter table option.** You can create a columnstore index on an existing memory-optimized table. Previously you could only create the columnstore index along with table creation.  
  
-   For more details, see [Columnstore Indexes Versioned Feature Summary](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Versioned-Feature-Summary.md).  
  
 **Parallel scan of nonclustered indexes on MEMORY_OPTIMIZED tables:** Now all [indexes on MEMORY_OPTIMIZED tables](../../Topics/TopicNameNotContainA/Guidelines-for-Using-Indexes-on-Memory-Optimized-Tables.md) support parallel scan. This speeds the performance of analytical queries that scan large sets of data.  
  
 **New Default Database Settings:** New values for the model database and default values for new databases (which are based on model). The initial size of the data and log files is now 8 MB. The default auto-growth of data and log files is now 64MB.  
  
 **Autogrow options:** Trace flag 1117 is replaced by the AUTOGROW_SINGLE_FILE and AUTOGROW_ALL_FILES option of ALTER DATABASE, and trace flag 1117 has no affect. For more information, see [ALTER DATABASE File and Filegroup Options (Transact-SQL)](assetId:///1f635762-f7aa-4241-9b7a-b51b22292b07) and the new is_autogrow_all_files column of [sys.filegroups (Transact-SQL)](assetId:///9e851f72-1f8e-4515-a25d-152ebc12ed56).  
  
 **Allocation of mixed extents:** For user databases, default allocation for the first 8 pages of an object will change from using mixed page extents to using uniform extents. Trace flag 1118 is replaced with the SET MIXED_PAGE_ALLOCATION option of ALTER DATABASE, and trace flag 1118 has no affect. For more information, see [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc), and the new `is_mixed_page_allocation_on` column of [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289).  
  
 **sys.dm_db_index_usage_stats:** Beginning with [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], entries in [sys.dm_db_index_usage_stats (Transact-SQL)](assetId:///d06a001f-0f72-4679-bc2f-66fff7958b86) are retained as they were prior to [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)].  
  
 **sys.dm_exec_input_buffer** Information about statements submitted to the input buffer can be returned by the new dynamic management function [sys.dm_exec_input_buffer (Transact-SQL)](assetId:///fb34a560-bde9-4ad9-aa96-0d4baa4fc104).  
  
 **SQL Server Management Tools:** SQL Server Management Tools is no longer installed from the main feature tree; for details see [Install SQL Server Management Tools with SSMS](../../Topics/TopicNameNotContainA/Install-SQL-Server-Management-Tools-with-SSMS.md).  
  
 **What's new for PolyBase**  
  
-   Support for the latest Cloudera distribution CDH5.5 on Linux.  
  
-   Support for public containers and blobs in Azure blob storage.  
  
 For more detailed what's new information and information on previous months, see [What's New in Database Engine](../../Topics/TopicNameNotContainA/What-s-New-in-Database-Engine.md).  
  
##  <a name="bkmk_ssas"></a> Analysis Services - new this month  
 For more detailed what's new information and information on previous months, see [What's New in Analysis Services](../../Topics/TopicNameNotContainA/What-s-New-in-Analysis-Services.md).  
  
### PowerShell for Tabular models at 1200 compatibility level  
 RC0 completes the PowerShell enhancements for Tabular models created at the SQL Server 2016 compatibility level (1200). You can use all of the applicable cmdlets, plus cmdlets specific to Tabular mode: [Invoke-ProcessASDatabase](../../Topics/TopicNameNotContainA/Invoke-ProcessASDatabase.md) and [Invoke-ProcessTable cmdlet](../../Topics/TopicNameNotContainA/Invoke-ProcessTable-cmdlet.md).  
  
### SSIS Tasks for Tabular models at 1200 compatibility level  
 SSIS tasks and destinations against a SQL Server 2016 tabular model use Tabular object representations instead of multidimensional. For example, in the latest SSDT, when you select objects to process, the Processing Task will automatically detect it is a Tabular model and show Tabular objects instead of measuregroups and dimensions.  
  
### Microsoft.AnalysisServices.Tabular namespace for Tabular 1200 programmability in AMO  
 Analysis Services Management objects is updated to include a new Tabular namespace for managing a Tabular instance of SQL Server 2016 Analysis Services (at compatibility level 1200), as well as provide the data definition language for creating or modifying Tabular models programmatically. Visit [Microsoft.AnalysisServices.Tabular](assetId:///4d6733fb-5736-4995-a3cf-fbc0380cbf5f) to read up on the API.  
  
### Display folders for Tabular models at 1200 compatibility level  
 Defined in SQL Server Data Tools and rendered in client applications like Excel or Power BI Desktop, display folders help you organize large numbers of measures into individual folders, adding a visual hierarchy for easier navigation in field lists.  
  
##  <a name="bkmk_ssis"></a> Integration Services - new this month  
 **SSIS Designer creates and maintains packages for SQL Server 2016, 2014, or 2012**. You can now use SSIS Designer in SQL Server Data Tools (SSDT) for Visual Studio 2015 to create and maintain packages that target SQL Server 2016, SQL Server 2014, or SQL Server 2012. In the property pages for an Integration Services project, on the **General** tab of **Configuration Properties**, select the **TargetServerVersion** property and choose SQL Server 2016, SQL Server 2014, or SQL Server 2012. To get SSDT, see [Download Latest SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
  
 **Support for server-wide default logging level**. In SQL Server **Server Properties**, under the **Server logging level** property, you can now select a default server-wide logging level. You can pick from one of the built-in logging levels - basic, none, verbose, performance, or runtime lineage - or you can pick an existing customized logging level. The selected logging level applies to all packages deployed to the SSIS Catalog. It also applies by default to a SQL Agent job step that runs an SSIS package.  
  
 **HDFS File Destination now supports ORC file format**. The HDFS File Destination now supports the ORC file format in addition to Text and Avro. (The HDFS File Source supports only Text and Avro.) For more info about this component, see [HDFS File Destination](../../Topics/TopicNameNotContainA/HDFS-File-Destination.md).  
  
 For more detailed what's new information and information on previous months, see [What's New in Integration Services](../../Topics/TopicNameNotContainA/What-s-New-in-Integration-Services.md).  
  
##  <a name="bkmk_mds"></a> Master Data Services - new this month  
 **Derived Hierarchy Management Experience Improved**  
  
 The derived hierarchy management experience in MDS has been improved. For more information about this feature, see [Create a Derived Hierarchy (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Derived-Hierarchy--Master-Data-Services-.md).  
  
 For more detailed what's information on previous months, see [What's New in Master Data Services (MDS)](../../Topics/TopicNameNotContainA/What-s-New-in-Master-Data-Services--MDS-.md).  
  
## Reporting Services - new this month  
 For more detailed what's new information and information on previous months, see [What's New in Reporting Services (SSRS)](../../Topics/TopicNameNotContainA/What-s-New-in-Reporting-Services--SSRS-.md).  
  
## SQL Server R Services  
 For more detailed what's new information and information on previous months, see [What's New in SQL Server R Services](../../Topics/TopicNameNotContainA/What-s-New-in-SQL-Server-R-Services.md).  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20What's%20New%20in%20SQL%20Server%202016%20page)  
  
## More information about SQL Server 2016  
 For more information about [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], or to download the [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] data sheet, see [SQL Server 2016 Preview](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/default.aspx).  
  
 ![Microsoft SQL Server 2016 data sheet](../../Topics/TopicNameNotContainA/images/SQLServer2016Datasheet.png "SQLServer2016Datasheet")