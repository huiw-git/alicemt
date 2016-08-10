---
title: "Manage and Monitor Full-Text Search for a Server Instance"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2733ed78-6d33-4bf9-94da-60c3141b87c8
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Manage and Monitor Full-Text Search for a Server Instance
Full-text administration for a server instance includes:  
  
-   System management tasks such as managing the FDHOST Launcher service (MSSQLFDLauncher), restarting filter daemon host process if you change the service account credentials, configuring server-wide full-text properties, and backing up full-text catalogs. At the server level, for example, you can specify a default full-text language that differs from the default language of the server instance as a whole.  
  
-   Configuring full-text linguistic components (word breakers and stemmers, thesaurus file, and stopwords and stoplists).  
  
-   Configuring a user database for full-text search. This involves creating one or more full-text catalogs for the database and defining a full-text index on each table or indexed view on which you want to execute full-text queries.  
  
##  <a name="props"></a> Viewing or Changing Server Properties for Full-Text Search  
 You can view the full-text properties of an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
#### To view and change server properties for full-text search  
  
1.  In Object Explorer, right-click a server, and then click **Properties**.  
  
2.  In the **Server Properties** dialog box, click the **Advanced** page to view server information about full-text search. The full-text properties are as follows:  
  
    -   **Default Full-Text Language**  
  
         Specifies a default language for full-text indexed columns. Linguistic analysis of full-text indexed data is dependent on the language of the data. The default value of this option is the language of the server. For the language that corresponds to the displayed setting, see [sys.fulltext_languages (Transact-SQL)](assetId:///2ed6b53d-1cf2-4763-9d58-36ea24a610ef).  
  
    -   **Full-Text Upgrade Option**  
  
         This server property controls how full-text indexes are migrated when upgrading a database from [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] to a later version. This property applies to upgrading by attaching a database, restoring a database backup, restoring a file backup, or copying the database by using the Copy Database Wizard.  
  
         The alternatives are as follows:  
  
         **Import**  
         Full-text catalogs are imported. Typically, import is significantly faster than rebuild. For example, when using only one CPU, import runs about 10 times faster than rebuild. However, an imported full-text catalog does not use the new and enhanced word breakers introduced in [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)], so you might want to rebuild your full-text catalogs eventually.  
  
        > [!NOTE]  
        >  Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.  
  
         If a full-text catalog is not available, the associated full-text indexes are rebuilt. This option is available for only [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] databases.  
  
         **Rebuild**  
         Full-text catalogs are rebuilt using the new and enhanced word breakers. Rebuilding indexes can take awhile, and a significant amount of CPU and memory might be required after the upgrade.  
  
         **Reset**  
         Full-text catalogs are reset. [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained. After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically. The catalog will remain empty until you manually issue a full population, after the upgrade completes.  
  
         For information about choosing a full-text upgrade option, see full-[Upgrade Full-Text Search](../../Topics/TopicNameNotContainA/Upgrade-Full-Text-Search.md).  
  
        > [!NOTE]  
        >  The full-text upgrade option can also be set by using the [sp_fulltext_service](assetId:///17a91433-f9b6-4a40-88c4-8c704ec2de9f)**upgrade_option** action.  
  
##  <a name="metadata"></a> Viewing Additional Full-Text Server Properties  
 [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] functions can be used to obtain the value of various server-level properties of full-text search. This information is useful for administrating and troubleshooting full-text search.  
  
 The following table lists full-text properties of a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] server instance and their related [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] functions.  
  
|Property|Description|Function|  
|--------------|-----------------|--------------|  
|**IsFullTextInstalled**|Whether the full-text component is installed with the current instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|[FULLTEXTSERVICEPROPERTY](assetId:///b7dcacb0-af83-4807-9d1e-49148b56b59c)<br /><br /> [SERVERPROPERTY](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a)|  
||||  
|**LoadOSResources**|Whether operating system word breakers and filters are registered and used with this instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|FULLTEXTSERVICEPROPERTY|  
|**VerifySignature**|Specifies whether only signed binaries are loaded by the Full-Text Engine.|FULLTEXTSERVICEPROPERTY|  
  
##  <a name="monitor"></a> Monitoring Full-Text Search Activity  
 Several dynamic management views and functions are useful monitoring full-text search activity on a server instance.  
  
 **To view information about the full-text catalogs with in-progress population activity**  
  
-   [sys.dm_fts_active_catalogs (Transact-SQL)](assetId:///40ab5453-040c-4d2e-bb49-e340cf90c3ee)  
  
 **To view current activity of a filter daemon host process**  
  
-   [sys.dm_fts_fdhosts (Transact-SQL)](assetId:///d42a6334-4362-4361-83da-f8324fe55ec7)  
  
 **To view information about in-progress index populations**  
  
-   [sys.dm_fts_index_population (Transact-SQL)](assetId:///82d1c102-efcc-4b60-9a5e-3eee299bcb2b)  
  
 **To view memory buffers in a memory pool that are used as part of a crawl or crawl range.**  
  
-   [sys.dm_fts_memory_buffers (Transact-SQL)](assetId:///56895fe5-e8df-4d75-9adc-c1f7757cdef8)  
  
 **To view the shared memory pools available to the full-text gatherer component for a full-text crawl or a full-text crawl range**  
  
-   [sys.dm_fts_memory_pools (Transact-SQL)](assetId:///24747239-cd78-4d55-a00a-19233a457f42)  
  
 **To view information about each full-text indexing batch**  
  
-   [sys.dm_fts_outstanding_batches (Transact-SQL)](assetId:///c4d697ed-c906-4c28-b137-036a25e13c84)  
  
 **To view information about the specific ranges related to an in-progress population**  
  
-   [sys.dm_fts_population_ranges (Transact-SQL)](assetId:///58d8564b-9c43-4965-a31c-2893890334ef)