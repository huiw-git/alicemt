---
title: "Semantic Search DDL, Functions, Stored Procedures, and Views"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Semantic Search DDL, Functions, Stored Procedures, and Views
Lists the Transact-SQL statements and the database objects that support statistical semantic search in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 For the list of statements and database objects that support full-text search, see [Full-Text Search DDL, Functions, Stored Procedures, and Views](../../Topics/TopicNameNotContainA/Full-Text-Search-DDL--Functions--Stored-Procedures--and-Views.md).  
  
##  <a name="ddl"></a> Transact-SQL Data Definition Language (DDL) Statements  
  
|Object|More Information|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX (Transact-SQL)](assetId:///b6fbe9e6-3033-4d1b-b6bf-1437baeefec3)|[Enable Semantic Search on Tables and Columns](../../Topics/TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[CREATE FULLTEXT INDEX (Transact-SQL)](assetId:///8b80390f-5f8b-4e66-9bcc-cabd653c19fd)|[Enable Semantic Search on Tables and Columns](../../Topics/TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
  
##  <a name="func"></a> System Functions  
  
|Object|More Information|  
|------------|----------------------|  
|[semantickeyphrasetable (Transact-SQL)](assetId:///d33b973a-2724-4d4b-aaf7-67675929c392)|[Find Key Phrases in Documents with Semantic Search](../../Topics/TopicNameNotContainA/Find-Key-Phrases-in-Documents-with-Semantic-Search.md)|  
|[semanticsimilaritydetailstable (Transact-SQL)](assetId:///038d751a-fca5-4b4c-9129-cba741a4e173)|[Find Similar and Related Documents with Semantic Search](../../Topics/TopicNameNotContainA/Find-Similar-and-Related-Documents-with-Semantic-Search.md)|  
|[semanticsimilaritytable (Transact-SQL)](assetId:///b49d40ab-7552-438b-ad67-6237dcccb75b)|[Find Similar and Related Documents with Semantic Search](../../Topics/TopicNameNotContainA/Find-Similar-and-Related-Documents-with-Semantic-Search.md)|  
  
##  <a name="meta"></a> System Metadata Functions  
  
|Object|More Information|  
|------------|----------------------|  
|[COLUMNPROPERTY (Transact-SQL)](assetId:///2408c264-6eca-4120-bb71-df043c7c2792)|[Enable Semantic Search on Tables and Columns](../../Topics/TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[DATABASEPROPERTYEX (Transact-SQL)](assetId:///8a9e0ffb-28b5-4640-95b2-a54e3e5ad941)|[Enable Semantic Search on Tables and Columns](../../Topics/TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[FULLTEXTCATALOGPROPERTY (Transact-SQL)](assetId:///f841dc79-2044-4863-aff0-56b8bb61f250)|[Manage and Monitor Semantic Search](../../Topics/TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[INDEXPROPERTY (Transact-SQL)](assetId:///998d5788-4871-44a8-8125-0d9390868b84)|[Manage and Monitor Semantic Search](../../Topics/TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[OBJECTPROPERTYEX (Transact-SQL)](assetId:///be36b3e3-3309-4332-bfb5-c7e9cf8dc8bd)|[Enable Semantic Search on Tables and Columns](../../Topics/TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[SERVERPROPERTY (Transact-SQL)](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a)|[Install and Configure Semantic Search](../../Topics/TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
  
##  <a name="sproc"></a> System Stored Procedures  
  
|Object|More Information|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)](assetId:///bef1b104-5a44-4327-9ae4-45eae3000f7e)|[Install and Configure Semantic Search](../../Topics/TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)](assetId:///1426ca4a-9a76-489e-98da-8f6d13ff9732)|[Install and Configure Semantic Search](../../Topics/TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
  
##  <a name="cv"></a> System Views – Catalog Views  
  
|Object|More Information|  
|------------|----------------------|  
|[sys.fulltext_index_columns (Transact-SQL)](assetId:///c34b8625-e53c-4281-ace6-d46230d5cb84)|[Manage and Monitor Semantic Search](../../Topics/TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[sys.fulltext_semantic_language_statistics_database (Transact-SQL)](assetId:///32e95614-ed88-4068-8c37-1e21544717bc)|[Install and Configure Semantic Search](../../Topics/TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
|[sys.fulltext_semantic_languages (Transact-SQL)](assetId:///b42a85e6-1db9-4a22-8a70-014574c95198)|[Install and Configure Semantic Search](../../Topics/TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
  
##  <a name="dmv"></a> System Views – Dynamic Management Views  
  
|Object|More Information|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats (Transact-SQL)](assetId:///997c3278-3630-47f6-ada3-190b6c16ce0e)|[Manage and Monitor Semantic Search](../../Topics/TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[sys.dm_fts_index_population (Transact-SQL)](assetId:///82d1c102-efcc-4b60-9a5e-3eee299bcb2b)|[Manage and Monitor Semantic Search](../../Topics/TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[sys.dm_fts_semantic_similarity_population (Transact-SQL)](assetId:///33666f28-c370-47e2-a932-190316ed5f69)|[Manage and Monitor Semantic Search](../../Topics/TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
  
## See Also  
 [Manage and Monitor Semantic Search](../../Topics/TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)