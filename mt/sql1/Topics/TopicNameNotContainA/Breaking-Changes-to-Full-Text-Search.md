---
title: "Breaking Changes to Full-Text Search"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c55a6748-e5d9-4fdb-9a1f-714475a419c5
caps.latest.revision: 63
caps.handback.revision: 0
manager: jhubbard
---
# Breaking Changes to Full-Text Search
This topic describes breaking changes in full-text search. These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. You might encounter these issues when you upgrade.  
  
## Breaking Changes in Full-Text Search in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]  
 Information to come later.  
  
## Breaking Changes in Full-Text Search in [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]  
 None.  
  
## Breaking Changes in Full-Text Search in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]  
  
### Collation Changed for name Column in sys.fulltext_languages  
 The collation of the language **name** column in the catalog view [sys.fulltext_languages (Transact-SQL)](assetId:///2ed6b53d-1cf2-4763-9d58-36ea24a610ef) has been changed from the fixed collation of the Resource database to the default collation selected for the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. This change makes it possible to compare the values in the **name** column when you join the [sys.syslanguages (Transact-SQL)](assetId:///f216d1cd-997c-42f0-a737-abbdfcd88383) view with **sys.fulltext_languages**. For example, you can query for all the databases where the default full-text language is different from the default database language.  
  
## See Also  
 [Behavior Changes to Full-Text Search](../../Topics/TopicNameNotContainA/Behavior-Changes-to-Full-Text-Search.md)   
 [Full-Text Search](../../Topics/TopicNameNotContainA/Full-Text-Search.md)