---
title: Features Supported by the Editions of SQL Server 2016
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
robots: noindex,nofollow
---
# Features Supported by the Editions of SQL Server 2016
  This topic provides details of features supported by the different editions of SQL Server [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 SQL Server Evaluation edition is available for a 180\-day trial period.  
  
> [!NOTE]  
>  To download [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], go to  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
  
 For features supported by Evaluation and Developer editions see SQL Server Enterprise Edition  
  
 To navigate the table for a SQL Server technology, click on its link:  
  
-   [Cross-Box Scale Limits](#Cross-BoxScaleLimits)  
  
-   [RDBMS High Availability](#RDBMSHA)  
  
-   [RDBMS Scalability and Performance](#RDBMSSP)  
  
-   [RDBMS Security](#RDBMSS)  
  
-   [Replication](#Replication)  
  
-   [Management Tools](#SSMS)  
  
-   [RDBMS Manageability](#RDBMSM)  
  
-   [Development Tools](#DevTools)  
  
-   [Programmability](#Programmability)  
  
-   [Integration Services](#IS)  
  
-   [Integration Services - Advanced Adapters](#ISAA)  
  
-   [Integration Services - Advanced Transforms](#ISAT)  
  
-   [Master Data Services](#MDS)  
  
-   [Data Warehouse](#DW)  
  
-   [Analysis Services](#SSAS)  
  
-   [BI Semantic Model (Multi Dimensional)](#BIMD)  
  
-   [BI Semantic Model (Tabular)](#BIT)  
  
-   [Power Pivot for SharePoint](#PPSP)  
  
-   [Data Mining](#DM)  
  
-   [Reporting Services](#SSRS)  
  
-   [Business Intelligence Clients](#BIC)  
  
-   [Spatial and Location Services](#SLS)  
  
-   [Additional Database Services](#ADS)  
  
-   [Other Components](#Other)  
  
##  <a name="Cross-BoxScaleLimits"></a> Cross\-Box Scale Limits  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Maximum compute capacity used by a single instance \- [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]<sup>1</sup>|Operating system maximum|Limited to lesser of 4 sockets or 24 cores|Limited to lesser of 4 sockets or 16 cores|Limited to lesser of 1 socket or 4 cores|Limited to lesser of 1 socket or 4 cores|Limited to lesser of 1 socket or 4 cores|Operating system maximum|  
|Maximum compute capacity used by a single instance \- [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] or [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]|Operating system maximum|Limited to lesser of 4 sockets or 24 cores|Limited to lesser of 4 sockets or 16 cores|Limited to lesser of 1 socket or 4 cores|Limited to lesser of 1 socket or 4 cores|Limited to lesser of 1 socket or 4 cores|Operating system maximum|  
|Maximum memory utilized per instance of [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|Operating System Maximum|128 GB|64 GB|1 GB|1 GB|1 GB|Operating System Maximum|  
|Maximum memory utilized per instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]|Operating System Maximum|Tabular: 16 GB<br /><br /> MOLAP: 64 GB|N\/A|N\/A|N\/A|N\/A|Operating System Maximum|  
|Maximum memory utilized per instance of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]|Operating System Maximum|64 GB|64 GB|4 GB|N\/A|N\/A|Operating System Maximum|  
|Maximum relational database size|524 PB|524 PB|524 PB|10 GB|10 GB|10 GB|524 PB|  
  
 1. Enterprise Edition with Server \+ Client Access License \(CAL\) based licensing \(not available for new agreements\) is limited to a maximum of 20 cores per SQL Server instance. There are no limits under the Core\-based Server Licensing model. For more information, see [Compute Capacity Limits by Edition of SQL Server](../../Topics\TopicNameNotContainA/Compute-Capacity-Limits-by-Edition-of-SQL-Server.md).  
  
##  <a name="RDBMSHA"></a> RDBMS High Availability  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Server core support <sup>1</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Log shipping|Yes|Yes|Yes|No|No|No|Yes|  
|Database mirroring|Yes|Yes<br /><br /> Full safety only|Witness only|Witness only|Witness only|Witness only|Yes|  
|Backup compression|Yes|Yes|||||Yes|  
|Database snapshot|Yes||||||Yes|  
|Always On failover cluster instances|Yes<br /><br /> Number of nodes is the operating system maximum|Yes<br /><br /> Support for 2 nodes|||||Yes<br /><br /> Number of nodes is the operating system maximum|  
|Always On availability groups|Yes<br /><br /> Up to 8 secondary replicas, including 2 synchronous secondary replicas||||||Yes|  
|Basic availability groups||Yes<br /><br /> Support for 2 nodes||||||  
|Connection director|Yes||||||Yes|  
|Online page and file restore|Yes||||||Yes|  
|Online indexing|Yes||||||Yes|  
|Online schema change|Yes||||||Yes|  
|Fast recovery|Yes||||||Yes|  
|Mirrored backups|Yes||||||Yes|  
|Hot add memory and CPU|Yes||||||Yes|  
|Database recovery advisor|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Encrypted backup|Yes|Yes|||||Yes|  
|Smart backup|Yes|Yes|||||Yes|  
  
 <sup>1</sup> For more information on installing SQL Server 2016 on Server Core,  see [Install SQL Server 2016 on Server Core](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-on-Server-Core.md).  
  
##  <a name="RDBMSSP"></a> RDBMS Scalability and Performance  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Operational analytics|Yes||||||Yes|  
|In\-Memory Column Store|Yes||||||Yes|  
|Stretch Database|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Persistent Main Memory|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Multi\-instance support|50|50|50|50|50|50|50|  
|Table and index partitioning|Yes||||||Yes|  
|Data compression|Yes||||||Yes|  
|Resource Governor|Yes||||||Yes|  
|Partition Table Parallelism|Yes||||||Yes|  
|Multiple Filestream containers|Yes||||||Yes|  
|NUMA Aware and Large Page Memory and Buffer Array Allocation|Yes||||||Yes|  
|Buffer Pool Extension|Yes|Yes|||||Yes|  
|IO Resource Governance|Yes||||||Yes|  
|In Memory OLTP|Yes||||||Yes|  
|Delayed Durability|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
  
##  <a name="RDBMSS"></a> RDBMS Security  
  
|Feature|Enterprise|Standard|Web|Express|Express with Advanced Services|Express with Tools|Developer|  
|-------------|----------------|--------------|---------|-------------|------------------------------------|------------------------|---------------|  
|Row\-level security|Yes|Yes|No||||Yes|  
|Always Encrypted|Yes||||||Yes|  
|Dynamic data masking|Yes|Yes|||||Yes|  
|Basic auditing|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Fine grained auditing|Yes||||||Yes|  
|Transparent database encryption|Yes||||||Yes|  
|Extensible key management|Yes||||||Yes|  
|User\-defined roles|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Contained databases|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Encryption for backups|Yes|Yes|||||Yes|  
  
##  <a name="Replication"></a> Replication  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Heterogeneous subscribers|Yes|Yes|||||Yes|  
|Merge replication|Yes|Yes|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes|  
|Oracle publishing|Yes||||||Yes|  
|Peer to peer transactional replication|Yes||||||Yes|  
|Snapshot replication|Yes|Yes|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes|  
|SQL Server change tracking|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Transactional replication|Yes|Yes|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes \(Subscriber only\)|Yes|  
|Transactional replication to Azure|Yes|Yes|Yes||||Yes|  
|Transactional replication updateable subscription|Yes||||||Yes|  
  
##  <a name="SSMS"></a> Management Tools  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|SQL Management Objects \(SMO\)|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|SQL Configuration Manager|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|SQL CMD \(Command Prompt tool\)|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|SQL Server Management Studio|Yes|Yes|Yes|Yes|Yes||Yes|  
|Distributed Replay \- Admin Tool|Yes|Yes|Yes|Yes|Yes||Yes|  
|Distribute Replay \- Client|Yes|Yes|Yes||||Yes|  
|Distributed Replay \- Controller|Yes \(Up to 16 clients\)|Yes \(1 client\)|Yes \(1 client\)||||Yes \(1 client\)|  
|SQL Profiler|Yes|Yes|No <sup>1</sup>|No <sup>1</sup>|No <sup>1</sup>|No <sup>1</sup>|Yes|  
|SQL Server Agent|Yes|Yes|Yes||||Yes|  
|Microsoft System Center Operations Manager Management Pack|Yes|Yes|Yes||||Yes|  
|Database Tuning Advisor \(DTA\)|Yes|Yes <sup>2</sup>|Yes <sup>2</sup>||||Yes|  
|Deploy a SQL Server Database to a Windows Azure VM Wizard|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|SQL Server Data Files in Windows Azure|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
  
 <sup>1</sup> SQL Server Web, SQL Server Express, SQL Server Express with Tools, and SQL Server Express with Advanced Services can be profiled using SQL Server Standard and SQL Server Enterprise editions.  
  
 <sup>2</sup> Tuning enabled only on Standard edition features  
  
##  <a name="RDBMSM"></a> RDBMS Manageability  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|User instances||||Yes|Yes|Yes|Yes|  
|LocalDB||||Yes|Yes||Yes|  
|Dedicated admin connection|Yes|Yes|Yes|Yes with trace flag|Yes with trace flag|Yes with trace flag|Yes|  
|PowerShell scripting support|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|SysPrep support <sup>1</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Support for data\-tier application component operations \- extract, deploy, upgrade, delete|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Policy automation \(check on schedule and change\)|Yes|Yes|Yes||||Yes|  
|Performance data collector|Yes|Yes|Yes||||Yes|  
|Able to enroll as a managed instance in multi\-instance management|Yes|Yes|Yes||||Yes|  
|Standard performance reports|Yes|Yes|Yes||||Yes|  
|Plan guides and plan freezing for plan guides|Yes|Yes|Yes||||Yes|  
|Direct query of indexed views \(using NOEXPAND hint\)|Yes|Yes|Yes||||Yes|  
|Automatic indexed views maintenance|Yes|Yes|Yes||||Yes|  
|Distributed partitioned views|Yes|Partial. Distributed partitioned views are not updatable|Partial. Distributed partitioned views are not updatable|Partial. Distributed partitioned views are not updatable|Partial. Distributed partitioned views are not updatable|Partial. Distributed partitioned views are not updatable|Yes|  
|Parallel indexed operations|Yes||||||Yes|  
|Automatic use of indexed view by query optimizer|Yes||||||Yes|  
|Parallel consistency check|Yes|||||||  
|SQL Server Utility Control Point|Yes||||||Yes|  
|Contained databases|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Buffer pool extension|Yes|Yes|||||Yes|  
  
 <sup>1</sup> For more information, see[Considerations for Installing SQL Server Using SysPrep](../../Topics\TopicNameNotContainA/Considerations-for-Installing-SQL-Server-Using-SysPrep.md).  
  
##  <a name="DevTools"></a> Development Tools  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Microsoft Visual Studio integration|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Intellisense \(Transact\-SQL and MDX\)|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|SQL Server Data Tools \(SSDT\)|Yes|Yes|Yes|Yes|||Yes|  
|SQL query edit and design tools|Yes|Yes|||||Yes|  
|Version control support|Yes|Yes|||||Yes|  
|MDX edit, debug, and design tools|Yes|Yes|||||Yes|  
  
##  <a name="Programmability"></a> Programmability  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Basic R integration|Yes|Yes|Yes|Yes|||Yes|  
|Advanced R integration|Yes||||||Yes|  
|R Server \(Standalone\)|Yes||||||Yes|  
|Polybase compute node|Yes|Yes|||||Yes|  
|Polybase head node|Yes|||||||  
|JSON|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Query Store|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Temporal|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Common Language Runtime \(CLR\) Integration|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Native XML support|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|XML indexing|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|MERGE & UPSERT capabilities|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|FILESTREAM support|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|FileTable|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Date and Time datatypes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Internationalization support|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Full\-text and semantic search|Yes|Yes|Yes|Yes|||Yes|  
|Specification of language in query|Yes|Yes|Yes|Yes|||Yes|  
|Service Broker \(messaging\)|Yes|Yes|No \(Client only\)|No \(Client only\)|No \(Client only\)|No \(Client only\)|Yes|  
|Transact\-SQL endpoints|Yes|Yes|Yes||||Yes|  
  
##  <a name="IS"></a> Integration Services  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|SQL Server Import and Export Wizard|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Built\-in data source connectors|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Azure data source connectors and tasks|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Hadoop \/ HDFS connectors and tasks|Yes|Yes|Yes||||Yes|  
|SSIS Designer and runtime|Yes|Yes|||||Yes|  
|Built in tasks and transformations|Yes|Yes|||||Yes|  
|Basic data profiling tools|Yes|Yes|||||Yes|  
|Change Data Capture Service for Oracle by Attunity|Yes||||||Yes|  
|Change Data Capture Designer for Oracle by Attunity|Yes||||||Yes|  
  
##  <a name="ISAA"></a> Integration Services \- Advanced Adapters  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|High performance Oracle destination|Yes||||||Yes|  
|High performance Teradata Destination|Yes||||||Yes|  
|SAP BW source and destination|Yes||||||Yes|  
|Data mining model training destination adapter|Yes||||||Yes|  
|Dimension processing destination adapter|Yes||||||Yes|  
|Partition processing destination adapter|Yes||||||Yes|  
|Change Data Capture components by Attunity|Yes||||||Yes|  
|Connector for Open Database Connectivity \(ODBC\) by Attunity|Yes||||||Yes|  
  
##  <a name="ISAT"></a> Integration Services \- Advanced Transforms  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Persistent \(high performance\) lookups|Yes||||||Yes|  
|Data mining query transformation|Yes||||||Yes|  
|Fuzzy grouping and lookup transformations|Yes||||||Yes|  
|Term extractions and lookup transformations|Yes||||||Yes|  
  
##  <a name="MDS"></a> Master Data Services  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database|Yes||||||Yes|  
|[!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application|Yes||||||Yes|  
  
##  <a name="DW"></a> Data Warehouse  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Create cubes without a database|Yes|Yes|||||Yes|  
|Auto\-generate staging and data warehouse schema|Yes|Yes|||||Yes|  
|Change data capture|Yes||||||Yes|  
|Star join query optimizations|Yes||||||Yes|  
|Scalable read\-only Analysis Services configuration|Yes||||||Yes|  
|Parallel query processing on partitioned tables and indexes|Yes||||||Yes|  
|xVelocity memory optimized columnstore indexes|Yes||||||Yes|  
|Global batch aggregation|Yes||||||Yes|  
  
##  <a name="SSAS"></a> Analysis Services  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Scalable shared databases|Yes||||||Yes|  
|Backup\/Restore & Attach\/Detach databases|Yes|Yes|||||Yes|  
|Synchronize databases|Yes||||||Yes|  
|Always On failover cluster instances|Yes<br /><br /> Number of nodes is the operating system maximum|Yes<br /><br /> Support for 2 nodes|||||Yes<br /><br /> Number of nodes is the operating system maximum|  
|Programmability \(AMO, ADOMD.Net, OLEDB, XML\/A, ASSL, TMSL\)|Yes|Yes|||||Yes|  
  
##  <a name="BIMD"></a> BI Semantic Model \(Multi Dimensional\)  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Semi\-additive measures|Yes|No <sup>1</sup>|||||Yes|  
|Hierarchies|Yes|Yes|||||Yes|  
|KPIs|Yes|Yes|||||Yes|  
|Perspectives|Yes||||||Yes|  
|Actions|Yes|Yes|||||Yes|  
|Account intelligence|Yes|Yes|||||Yes|  
|Time intelligence|Yes|Yes|||||Yes|  
|Custom rollups|Yes|Yes|||||Yes|  
|Writeback cube|Yes|Yes|||||Yes|  
|Writeback dimensions|Yes||||||Yes|  
|Writeback cells|Yes|Yes|||||Yes|  
|Drillthrough|Yes|Yes|||||Yes|  
|Advanced hierarchy types \(parent\-child and ragged hierarchies\)|Yes|Yes|||||Yes|  
|Advanced dimensions \(reference dimensions, many\-to\-many dimensions\)|Yes|Yes|||||Yes|  
|Linked measures and dimensions|Yes||||||Yes|  
|Translations|Yes|Yes|||||Yes|  
|Aggregations|Yes|Yes|||||Yes|  
|Multiple partitions|Yes|Yes, up to 3|||||Yes|  
|Proactive caching|Yes||||||Yes|  
|Custom assemblies \(stored procedures\)|Yes|Yes|||||Yes|  
|MDX queries and scripts|Yes|Yes|||||Yes|  
|DAX queries|Yes|Yes|||||Yes|  
|Role\-based security model|Yes|Yes|||||Yes|  
|Dimension and cell\-level security|Yes|Yes|||||Yes|  
|Scalable string storage|Yes|Yes|||||Yes|  
|MOLAP, ROLAP, and HOLAP storage models|Yes|Yes|||||Yes|  
|Binary and compressed XML transport|Yes|Yes|||||Yes|  
|Push\-mode processing|Yes||||||Yes|  
|Direct writeback|Yes||||||Yes|  
|Measure expressions|Yes||||||Yes|  
  
 <sup>1</sup> The LastChild semi\-additive measure is supported in Standard edition, but other semi\-additive measures, such as None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren, and ByAccount, are not. Additive measures, such as Sum, Count, Min, Max, and non\-additive measures \(DistinctCount\) are supported on all editions.  
  
##  <a name="BIT"></a> BI Semantic Model \(Tabular\)  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Hierarchies|Yes|Yes|||||Yes|  
|KPIs|Yes|Yes|||||Yes|  
|Perspectives|Yes||||||Yes|  
|Translations|Yes|Yes|||||Yes|  
|DAX calculations, DAX queries, MDX queries|Yes|Yes|||||Yes|  
|Row\-level security|Yes|Yes|||||Yes|  
|Multiple partitions|Yes||||||Yes|  
|In\-memory storage mode|Yes|Yes|||||Yes|  
|DirectQuery storage mode|Yes||||||Yes|  
  
##  <a name="PPSP"></a> Power Pivot for SharePoint  
  
|Feature|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|SharePoint farm integration based on shared service architecture|Yes||||||Yes|  
|Usage reporting|Yes||||||Yes|  
|Health monitoring rules|Yes||||||Yes|  
|Power Pivot gallery|Yes||||||Yes|  
|Power Pivot data refresh|Yes||||||Yes|  
|Power Pivot data feeds|Yes||||||Yes|  
  
##  <a name="DM"></a> Data Mining  
  
|Feature Name|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Standard algorithms|Yes|Yes|||||Yes|  
|Data mining tools \(Wizards, Editors,  Query Builders\)|Yes|Yes|||||Yes|  
|Cross validation|Yes||||||Yes|  
|Models on filtered subsets of mining structure data|Yes||||||Yes|  
|Time series: Custom blending between ARTXP and ARIMA methods|Yes||||||Yes|  
|Time series: Prediction with new data|Yes||||||Yes|  
|Unlimited concurrent DM queries|Yes||||||Yes|  
|Advanced configuration & tuning options for data mining algorithms|Yes||||||Yes|  
|Support for plug\-in algorithms|Yes||||||Yes|  
|Parallel model processing|Yes||||||Yes|  
|Time series: cross\-series prediction|Yes||||||Yes|  
|Unlimited attributes for association rules|Yes||||||Yes|  
|Sequence prediction|Yes||||||Yes|  
|Multiple prediction targets for naïve Bayes, neural network and logistic regression|Yes||||||Yes|  
  
##  <a name="SSRS"></a> Reporting Services  
  
|Feature Name|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Mobile reports and KPIs|Yes||||||Yes|  
|Supported catalog DB [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition|Standard or higher|Standard or higher|Web|Express|||Standard or higher|  
|Supported data source [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition|All   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] editions|All [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] editions|Web|Express|||All [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] editions|  
|Report server|Yes|Yes|Yes|Yes|||Yes|  
|Report designer|Yes|Yes|Yes|Yes|||Yes|  
|Report designer web portal|Yes|Yes|Yes|Yes|||Yes|  
|Role based security|Yes|Yes|Yes|Yes|||Yes|  
|Export to  Excel, PowerPoint, Word, PDF, and images|Yes|Yes|Yes|Yes|||Yes|  
|Enhanced gauges and charting|Yes|Yes|Yes|Yes|||Yes|  
|Pin report items to [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)]dashboards|Yes|Yes|Yes|Yes|||Yes|  
|Custom authentication|Yes|Yes|Yes|Yes|||Yes|  
|Report as data feeds|Yes|Yes|Yes|Yes|||Yes|  
|Model support|Yes|Yes|Yes||||Yes|  
|Create custom roles for role\-based security|Yes|Yes|||||Yes|  
|Model Item security|Yes|Yes|||||Yes|  
|Infinite click through|Yes|Yes|||||Yes|  
|Shared component library|Yes|Yes|||||Yes|  
|Email and file share subscriptions and scheduling|Yes|Yes|||||Yes|  
|Report history, execution snapshots and caching|Yes|Yes|||||Yes|  
|SharePoint Integration|Yes|Yes|||||Yes|  
|Remote and non\-SQL data source support<sup>1</sup>|Yes|Yes|||||Yes|  
|Data source, delivery and rendering, RDCE extensibility|Yes|Yes|||||Yes|  
|Custom branding|Yes||||||Yes|  
|Data driven report subscription|Yes||||||Yes|  
|Scale out deployment \(Web farms\)|Yes||||||Yes|  
|Alerting<sup>2</sup>|Yes||||||Yes|  
|[!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)] <sup>2</sup>|Yes||||||Yes|  
  
 <sup>1</sup> For more information on supported datasources in SQL Server 2016 Reporting Services \(SSRS\), see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md).  
  
 <sup>2</sup> Requires Reporting Services in SharePoint mode. For more information, see [Install Reporting Services SharePoint Mode](../../Topics\TopicNameNotContainA/Install-Reporting-Services-SharePoint-Mode.md).  
  
## Report Server Database Server Edition Requirements  
 When creating a report server database, not all editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can be used to host the database. The following table shows you which editions of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] you can use for specific editions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
|For this edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Reporting Services|Use this edition of the Database Engine instance to host the database|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Enterprise,  or Standard  editions \(local or remote\)|  
|Standard|Enterprise,  or Standard  editions \(local or remote\)|  
|Web|Web edition \(local only\)|  
|Express with Advanced Services|Express with Advanced Services \(local only\).|  
|Evaluation|Evaluation|  
  
##  <a name="BIC"></a> Business Intelligence Clients  
 The following software client applications are available on the Microsoft Download center and are provided to assist you with creating business intelligence documents that run on a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. When you host these documents in a server environment, use an edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that supports that document type. The following table identifies which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition contains the server features required to host the documents created in these client applications.  
  
|Tool Name|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] \(.rdlx\)|Yes|Yes|||||Yes|  
|Data Mining Add\-ins for Excel and Visio 2010 \(.xlsx, .vsdx\)|Yes|Yes|||||Yes|  
|[!INCLUDE[ssGeminiClient](../../Token\Other/ssGeminiClient_md.md)] 2010 and 2013 \(.xlsx\)|Yes||||||Yes|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)] \(.xlsx\)|Yes||||||Yes|  
|[!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Long_md.md)] \(.rsmobile\)|Yes||||||Yes|  
|Power BI apps for mobile devices \(iOS, Windows 10, Android\) \(.rsmobile\)|Yes||||||Yes|  
  
> [!NOTE]  
>  1.  [!INCLUDE[ssGeminiClient](../../Token\Other/ssGeminiClient_md.md)] is an Excel add\-in for creating workbooks with a data model.  [!INCLUDE[ssGeminiClient](../../Token\Other/ssGeminiClient_md.md)] does not depend on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], but [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] is required for sharing and collaborating on Excel workbooks with a data model in SharePoint. This capability is available as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Enterprise edition.  
>   
>      In Excel 2016, Power Pivot capability is built in, so you no longer need the Power Pivot add\-in.  
> 2.  The above table identifies the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] editions that are required to enable these client tools; however these tools can access data hosted on any edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
> 3.  [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Long_md.md)] is the single point for creation of mobile reports. Connect to  a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] server to access data sources and create reports. Then publish them to the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] server for others in the organization to access, either on the server or on mobile devices. You can also use [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Long_md.md)] stand alone with local data sources  
> 4.  Whether you are using  [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] on\-premises, [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] in the cloud, or both as your report delivery solution you only need one mobile app to access dashboards and mobile reports on mobile devices. The [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] apps are available for download from the Windows, iOS, or Android app stores.  
  
##  <a name="SLS"></a> Spatial and Location Services  
  
|Feature Name|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Spatial indexes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Planar and geodetic datatypes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Advanced spatial libraries|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Import\/export of industry\-standard spatial data formats|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
  
##  <a name="ADS"></a> Additional Database Services  
  
|Feature Name|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Migration Assistant|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Database mail|Yes|Yes|Yes||||Yes|  
  
##  <a name="Other"></a> Other Components  
  
|Feature Name|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Data Quality Services|Yes||||||Yes|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition||||StreamInsight Premium Edition|  
|StreamInsight HA|StreamInsight Premium Edition||||||StreamInsight Premium Edition|  
  
## See Also  
  
## See Also  
 [Product Specifications for SQL Server 2016](../../Topics\TopicNameNotContainA/Product-Specifications-for-SQL-Server-2016.md)   
 [Installation for SQL Server 2016](../../Topics\TopicNameNotContainA/Installation-for-SQL-Server-2016.md)  
  
  