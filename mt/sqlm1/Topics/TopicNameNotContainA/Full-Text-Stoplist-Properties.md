---
title: Full-Text Stoplist Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
---
# Full-Text Stoplist Properties
  Use this dialog box to add or delete individual stopwords, delete all stopwords for a specific language, or clear the current stoplist. A stopword is a commonly used word that is included in a stoplist. The stopwords in a stoplist are omitted from full\-text indexing for tables that use the stoplist. For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../../Topics\TopicNameNotContainA/Configure-and-Manage-Stopwords-and-Stoplists-for-Full-Text-Search.md).  
  
 **To use SQL Server Management Studio to change stoplist properties**  
  
-   [Configure and Manage Stopwords and Stoplists for Full-Text Search](../../Topics\TopicNameNotContainA/Configure-and-Manage-Stopwords-and-Stoplists-for-Full-Text-Search.md)  
  
## Options  
 **Action**  
 Specifies the action that you want to perform.  
  
 **Add stopword**  
 Add a commonly used word to the stoplist.  
  
 **Delete stopword**  
 Delete a stopword from the stoplist.  
  
 **Delete all stopwords**  
 Delete all the stopwords for a specific language.  
  
 **Clear stoplist**  
 Clear the stoplist by deleting all the stopwords for all languages.  
  
 **Stopword**  
 If you selected **Add stopword** or **Delete stopword**, enter the stopword in the **Stopword** field. A new stopword must be unique; that is, not yet in this stoplist for the language that you select.  
  
 **Full\-text language**  
 If you selected **Add stopword**, **Delete stopword**, or **Delete all stopwords**, select the language of the stopword or stopwords from the list box. This lists all the full\-text languages that are supported by the server instance.  
  
## See Also  
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../Topic/sys.fulltext_stopwords%20\(Transact-SQL\).md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../Topic/sys.fulltext_stoplists%20\(Transact-SQL\).md)   
 [Configure and Manage Stopwords and Stoplists for Full-Text Search](../../Topics\TopicNameNotContainA/Configure-and-Manage-Stopwords-and-Stoplists-for-Full-Text-Search.md)   
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../Topic/ALTER%20FULLTEXT%20STOPLIST%20\(Transact-SQL\).md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../Topic/CREATE%20FULLTEXT%20STOPLIST%20\(Transact-SQL\).md)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../Topic/DROP%20FULLTEXT%20STOPLIST%20\(Transact-SQL\).md)  
  
  