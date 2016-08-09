---
title: "Full-Text Stoplist Properties"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Full-Text Stoplist Properties
Use this dialog box to add or delete individual stopwords, delete all stopwords for a specific language, or clear the current stoplist. A stopword is a commonly used word that is included in a stoplist. The stopwords in a stoplist are omitted from full-text indexing for tables that use the stoplist. For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../../Topics/TopicNameNotContainA/Configure-and-Manage-Stopwords-and-Stoplists-for-Full-Text-Search.md).  
  
 **To use SQL Server Management Studio to change stoplist properties**  
  
-   [Configure and Manage Stopwords and Stoplists for Full-Text Search](../../Topics/TopicNameNotContainA/Configure-and-Manage-Stopwords-and-Stoplists-for-Full-Text-Search.md)  
  
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
  
 **Full-text language**  
 If you selected **Add stopword**, **Delete stopword**, or **Delete all stopwords**, select the language of the stopword or stopwords from the list box. This lists all the full-text languages that are supported by the server instance.  
  
## See Also  
 [sys.fulltext_stopwords (Transact-SQL)](assetId:///79787bb7-d729-448e-b56a-0a467bbb304f)   
 [sys.fulltext_stoplists (Transact-SQL)](assetId:///eb69fb8f-f6d9-446e-83c0-67afd05dfba0)   
 [Configure and Manage Stopwords and Stoplists for Full-Text Search](../../Topics/TopicNameNotContainA/Configure-and-Manage-Stopwords-and-Stoplists-for-Full-Text-Search.md)   
 [ALTER FULLTEXT STOPLIST (Transact-SQL)](assetId:///f6ad87d5-6a34-435a-8456-8244947c5c83)   
 [CREATE FULLTEXT STOPLIST (Transact-SQL)](assetId:///0669b1d0-46cc-4fac-8df7-5f7fa7af5db4)   
 [DROP FULLTEXT STOPLIST (Transact-SQL)](assetId:///3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15)