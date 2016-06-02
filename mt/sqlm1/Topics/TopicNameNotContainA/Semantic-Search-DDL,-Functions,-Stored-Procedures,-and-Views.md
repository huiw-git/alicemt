---
title: Semantic Search DDL, Functions, Stored Procedures, and Views
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
---
# Semantic Search DDL, Functions, Stored Procedures, and Views
  Lists the Transact\-SQL statements and the database objects that support statistical semantic search in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 For the list of statements and database objects that support full\-text search, see [Full-Text Search DDL, Functions, Stored Procedures, and Views](../../Topics\TopicNameNotContainA/Full-Text-Search-DDL,-Functions,-Stored-Procedures,-and-Views.md).  
  
##  <a name="ddl"></a> Transact\-SQL Data Definition Language \(DDL\) Statements  
  
|Object|More Information|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../Topic/ALTER%20FULLTEXT%20INDEX%20\(Transact-SQL\).md)|[Enable Semantic Search on Tables and Columns](../../Topics\TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../Topic/CREATE%20FULLTEXT%20INDEX%20\(Transact-SQL\).md)|[Enable Semantic Search on Tables and Columns](../../Topics\TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
  
##  <a name="func"></a> System Functions  
  
|Object|More Information|  
|------------|----------------------|  
|[semantickeyphrasetable &#40;Transact-SQL&#41;](../Topic/semantickeyphrasetable%20\(Transact-SQL\).md)|[Find Key Phrases in Documents with Semantic Search](../../Topics\TopicNameNotContainA/Find-Key-Phrases-in-Documents-with-Semantic-Search.md)|  
|[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../Topic/semanticsimilaritydetailstable%20\(Transact-SQL\).md)|[Find Similar and Related Documents with Semantic Search](../../Topics\TopicNameNotContainA/Find-Similar-and-Related-Documents-with-Semantic-Search.md)|  
|[semanticsimilaritytable &#40;Transact-SQL&#41;](../Topic/semanticsimilaritytable%20\(Transact-SQL\).md)|[Find Similar and Related Documents with Semantic Search](../../Topics\TopicNameNotContainA/Find-Similar-and-Related-Documents-with-Semantic-Search.md)|  
  
##  <a name="meta"></a> System Metadata Functions  
  
|Object|More Information|  
|------------|----------------------|  
|[COLUMNPROPERTY &#40;Transact-SQL&#41;](../Topic/COLUMNPROPERTY%20\(Transact-SQL\).md)|[Enable Semantic Search on Tables and Columns](../../Topics\TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../Topic/DATABASEPROPERTYEX%20\(Transact-SQL\).md)|[Enable Semantic Search on Tables and Columns](../../Topics\TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../Topic/FULLTEXTCATALOGPROPERTY%20\(Transact-SQL\).md)|[Manage and Monitor Semantic Search](../../Topics\TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[INDEXPROPERTY &#40;Transact-SQL&#41;](../Topic/INDEXPROPERTY%20\(Transact-SQL\).md)|[Manage and Monitor Semantic Search](../../Topics\TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../Topic/OBJECTPROPERTYEX%20\(Transact-SQL\).md)|[Enable Semantic Search on Tables and Columns](../../Topics\TopicNameNotContainA/Enable-Semantic-Search-on-Tables-and-Columns.md)|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md)|[Install and Configure Semantic Search](../../Topics\TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
  
##  <a name="sproc"></a> System Stored Procedures  
  
|Object|More Information|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](../Topic/sp_fulltext_semantic_register_language_statistics_db%20\(Transact-SQL\).md)|[Install and Configure Semantic Search](../../Topics\TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](../Topic/sp_fulltext_semantic_unregister_language_statistics_db%20\(Transact-SQL\).md)|[Install and Configure Semantic Search](../../Topics\TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
  
##  <a name="cv"></a> System Views – Catalog Views  
  
|Object|More Information|  
|------------|----------------------|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](../Topic/sys.fulltext_index_columns%20\(Transact-SQL\).md)|[Manage and Monitor Semantic Search](../../Topics\TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../Topic/sys.fulltext_semantic_language_statistics_database%20\(Transact-SQL\).md)|[Install and Configure Semantic Search](../../Topics\TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
|[sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](../Topic/sys.fulltext_semantic_languages%20\(Transact-SQL\).md)|[Install and Configure Semantic Search](../../Topics\TopicNameNotContainA/Install-and-Configure-Semantic-Search.md)|  
  
##  <a name="dmv"></a> System Views – Dynamic Management Views  
  
|Object|More Information|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_db_fts_index_physical_stats%20\(Transact-SQL\).md)|[Manage and Monitor Semantic Search](../../Topics\TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](../Topic/sys.dm_fts_index_population%20\(Transact-SQL\).md)|[Manage and Monitor Semantic Search](../../Topics\TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
|[sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../Topic/sys.dm_fts_semantic_similarity_population%20\(Transact-SQL\).md)|[Manage and Monitor Semantic Search](../../Topics\TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)|  
  
## See Also  
 [Manage and Monitor Semantic Search](../../Topics\TopicNameNotContainA/Manage-and-Monitor-Semantic-Search.md)  
  
  