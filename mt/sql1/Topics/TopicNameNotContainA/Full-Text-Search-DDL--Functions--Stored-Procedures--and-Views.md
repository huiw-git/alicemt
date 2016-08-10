---
title: "Full-Text Search DDL, Functions, Stored Procedures, and Views"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98c36715-4195-482e-a4a3-d93ff65b75f1
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Full-Text Search DDL, Functions, Stored Procedures, and Views
Lists the Transact-SQL statements and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database objects that support full-text search, including the property search feature.  
  
 This list does not include deprecated objects.  
  
 For the list of database objects that support semantic search, see [Semantic Search DDL, Functions, Stored Procedures, and Views](../../Topics/TopicNameNotContainA/Semantic-Search-DDL--Functions--Stored-Procedures--and-Views.md).  
  
##  <a name="ddl"></a> Transact-SQL Data Definition Language (DDL) Statements  
  
-   [CREATE FULLTEXT CATALOG (Transact-SQL)](assetId:///d7a8bd93-e2d7-4a40-82ef-39069e65523b)  
  
-   [CREATE FULLTEXT INDEX (Transact-SQL)](assetId:///8b80390f-5f8b-4e66-9bcc-cabd653c19fd)  
  
-   [CREATE FULLTEXT STOPLIST (Transact-SQL)](assetId:///0669b1d0-46cc-4fac-8df7-5f7fa7af5db4)  
  
-   [CREATE SEARCH PROPERTY LIST (Transact-SQL)](assetId:///5440cbb8-3403-4d27-a2f9-8e1f5a1bc12b)  
  
-   [ALTER FULLTEXT CATALOG (Transact-SQL)](assetId:///31a47aaf-6c7f-48a4-a86a-d57aec66c9cb)  
  
-   [ALTER FULLTEXT INDEX (Transact-SQL)](assetId:///b6fbe9e6-3033-4d1b-b6bf-1437baeefec3)  
  
-   [ALTER FULLTEXT STOPLIST (Transact-SQL)](assetId:///f6ad87d5-6a34-435a-8456-8244947c5c83)  
  
-   [ALTER SEARCH PROPERTY LIST (Transact-SQL)](assetId:///0436e4a8-ca26-4d23-93f1-e31e2a1c8bfb)  
  
-   [DROP FULLTEXT CATALOG (Transact-SQL)](assetId:///b54efb0b-400b-49ce-923b-ce20a2a12255)  
  
-   [DROP FULLTEXT INDEX (Transact-SQL)](assetId:///7443a4ab-1d43-4a22-bbba-a07f620892cb)  
  
-   [DROP FULLTEXT STOPLIST (Transact-SQL)](assetId:///3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15)  
  
-   [DROP SEARCH PROPERTY LIST (Transact-SQL)](assetId:///7c7ce52a-6b77-4a1c-9abf-d5feb664bea8)  
  
##  <a name="func"></a> System Predicates and Functions  
  
-   [CONTAINS (Transact-SQL)](assetId:///996c72fc-b1ab-4c96-bd12-946be9c18f84)  
  
-   [CONTAINSTABLE (Transact-SQL)](assetId:///e580c210-cf57-419d-9544-7f650f2ab814)  
  
-   [FREETEXT (Transact-SQL)](assetId:///2f199d3c-440e-4bcf-bdb5-82bb3994005d)  
  
-   [FREETEXTTABLE (Transact-SQL)](assetId:///4523ae15-4260-40a7-a53c-8df15e1fee79)  
  
##  <a name="meta"></a> System Metadata Functions  
  
-   [COLUMNPROPERTY (Transact-SQL)](assetId:///2408c264-6eca-4120-bb71-df043c7c2792)  
  
-   [FULLTEXTCATALOGPROPERTY (Transact-SQL)](assetId:///f841dc79-2044-4863-aff0-56b8bb61f250)  
  
-   [FULLTEXTSERVICEPROPERTY (Transact-SQL)](assetId:///b7dcacb0-af83-4807-9d1e-49148b56b59c)  
  
-   [INDEXPROPERTY (Transact-SQL)](assetId:///998d5788-4871-44a8-8125-0d9390868b84)  
  
-   [OBJECTPROPERTY (Transact-SQL)](assetId:///27569888-f8b5-4cec-a79f-6ea6d692b4ae)  
  
-   [OBJECTPROPERTYEX (Transact-SQL)](assetId:///be36b3e3-3309-4332-bfb5-c7e9cf8dc8bd)  
  
-   [SERVERPROPERTY (Transact-SQL)](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a)  
  
##  <a name="proc"></a> System Stored Procedures  
  
-   [sp_fulltext_keymappings (Transact-SQL)](assetId:///2818fa42-072d-4664-a2f7-7ec363b51d81)  
  
-   [sp_fulltext_load_thesaurus_file (Transact-SQL)](assetId:///73a309c3-6d22-42dc-a6fe-8a63747aa2e4)  
  
-   [sp_fulltext_pendingchanges (Transact-SQL)](assetId:///fee042fe-4781-4a33-a01b-d98fb5629f1b)  
  
-   [sp_fulltext_service (Transact-SQL)](assetId:///17a91433-f9b6-4a40-88c4-8c704ec2de9f)  
  
-   [sp_help_fulltext_system_components (Transact-SQL)](assetId:///ac1fc7a0-7f46-4a12-8c5c-8d378226a8ce)  
  
##  <a name="cat"></a> System Views – Catalog Views  
  
-   [sys.fulltext_catalogs (Transact-SQL)](assetId:///cf1489ff-4819-41fa-a62a-4ed797a16207)  
  
-   [sys.fulltext_document_types (Transact-SQL)](assetId:///156fcfa4-7304-4a5c-b96f-1c3e061e5df0)  
  
-   [sys.fulltext_index_catalog_usages (Transact-SQL)](assetId:///d095ab62-270b-484b-a541-9f9e7c951cf0)  
  
-   [sys.fulltext_index_columns (Transact-SQL)](assetId:///c34b8625-e53c-4281-ace6-d46230d5cb84)  
  
-   [sys.fulltext_index_fragments (Transact-SQL)](assetId:///a82e5018-5d88-45c0-9a47-c251e17a6cdb)  
  
-   [sys.fulltext_indexes (Transact-SQL)](assetId:///7fc10fdc-370f-4927-bba0-b76108a7508e)  
  
-   [sys.fulltext_languages (Transact-SQL)](assetId:///2ed6b53d-1cf2-4763-9d58-36ea24a610ef)  
  
-   [sys.fulltext_stoplists (Transact-SQL)](assetId:///eb69fb8f-f6d9-446e-83c0-67afd05dfba0)  
  
-   [sys.fulltext_stopwords (Transact-SQL)](assetId:///79787bb7-d729-448e-b56a-0a467bbb304f)  
  
-   [sys.fulltext_system_stopwords (Transact-SQL)](assetId:///487de53f-c637-4d78-85f6-fef5e768cd0c)  
  
-   [sys.registered_search_properties (Transact-SQL)](assetId:///1b9a7a5c-8c05-4819-83c3-7487dd08fcf7)  
  
-   [sys.registered_search_property_lists (Transact-SQL)](assetId:///630d4caa-9bea-4cd3-a5b1-01098b0855fc)  
  
##  <a name="dmv"></a> System Views – Dynamic Management Views  
  
-   [sys.dm_fts_active_catalogs (Transact-SQL)](assetId:///40ab5453-040c-4d2e-bb49-e340cf90c3ee)  
  
-   [sys.dm_fts_fdhosts (Transact-SQL)](assetId:///d42a6334-4362-4361-83da-f8324fe55ec7)  
  
-   [sys.dm_fts_index_keywords (Transact-SQL)](assetId:///fce7b2a1-7e74-4769-86a8-c77c7628decd)  
  
-   [sys.dm_fts_index_keywords_by_document (Transact-SQL)](assetId:///793b978b-c8a1-428c-90c2-a3e49d81b5c9)  
  
-   [sys.dm_fts_index_keywords_by_property (Transact-SQL)](assetId:///fa41e052-a79a-4194-9b1a-2885f7828500)  
  
-   [sys.dm_fts_index_population (Transact-SQL)](assetId:///82d1c102-efcc-4b60-9a5e-3eee299bcb2b)  
  
-   [sys.dm_fts_memory_buffers (Transact-SQL)](assetId:///56895fe5-e8df-4d75-9adc-c1f7757cdef8)  
  
-   [sys.dm_fts_memory_pools (Transact-SQL)](assetId:///24747239-cd78-4d55-a00a-19233a457f42)  
  
-   [sys.dm_fts_outstanding_batches (Transact-SQL)](assetId:///c4d697ed-c906-4c28-b137-036a25e13c84)  
  
-   [sys.dm_fts_parser (Transact-SQL)](assetId:///2736d376-fb9d-4b28-93ef-472b7a27623a)  
  
-   [sys.dm_fts_population_ranges (Transact-SQL)](assetId:///58d8564b-9c43-4965-a31c-2893890334ef)