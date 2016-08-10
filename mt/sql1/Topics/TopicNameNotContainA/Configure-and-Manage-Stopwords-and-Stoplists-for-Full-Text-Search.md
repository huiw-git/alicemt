---
title: "Configure and Manage Stopwords and Stoplists for Full-Text Search"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
caps.latest.revision: 80
caps.handback.revision: 0
manager: jhubbard
---
# Configure and Manage Stopwords and Stoplists for Full-Text Search
To prevent a full-text index from becoming bloated, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] has a mechanism that discards commonly occurring strings that do not help the search. These discarded strings are called *stopwords*. During index creation, the Full-Text Engine omits stopwords from the full-text index. This means that full-text queries will not search on stopwords.  
  
##  <a name="understand"></a> Understanding Stopwords and Stoplists  
 A stopword can be a word with meaning in a specific language, or it can be a *token* that does not have linguistic meaning. For example, in the English language, words such as "a," "and," "is," and "the" are left out of the full-text index since they are known to be useless to a search.  
  
 Although it ignores the inclusion of stopwords, the full-text index does take into account their position. For example, consider the phrase, "Instructions are applicable to these Adventure Works Cycles models". The following table depicts the position of the words in the phrase:  
  
|Word|Position|  
|----------|--------------|  
|Instructions|1|  
|are|2|  
|applicable|3|  
|to|4|  
|these|5|  
|Adventure|6|  
|Works|7|  
|Cycles|8|  
|models|9|  
  
 The stopwords "are", "to", and "these" that are in positions 2, 4, and 5 are left out of the full-text index. However, their positional information is maintained, thereby leaving the position of the other words in the phrase unaffected.  
  
 Stopwords are managed in databases using objects called stoplists. A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="creating"></a> Creating a Stoplist  
 You can create a stoplist in any of the following ways:  
  
-   Using the system-supplied stoplist in the database. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] ships with a system stoplist that contains the most commonly used stopwords for each supported language, that is for every language that is associated with given word breakers by default. The system stoplist contains common stopwords for all supported languages.  You can copy the system stoplist, and customize your copy by adding and removing stopwords.  
  
     The system stoplist is installed in the [Resource](../../Topics/TopicNameNotContainA/Resource-Database.md) database.  
  
-   Creating your own stoplist, and then adding stopwords to it for any language that you specify. You can also drop stopwords from your stoplist when necessary.  
  
-   Using an existing custom stoplist from any other database in the current server instance and then adding and dropping stopwords as necessary.  
  
 **To create a stoplist**  
  
-   [CREATE FULLTEXT STOPLIST (Transact-SQL)](assetId:///0669b1d0-46cc-4fac-8df7-5f7fa7af5db4)  
  
#### To create a full-text stoplist in Management Studio  
  
1.  In Object Explorer, expand the server.  
  
2.  Expand **Databases**, and then expand the database in which you want to create the full-text stoplist.  
  
3.  Expand **Storage**, and then right-click **Full-Text Stoplists**.  
  
4.  Select **New Full-Text Stoplist**.  
  
5.  Specify the stoplist name.  
  
6.  Optionally, specify someone else as the stoplist owner.  
  
7.  Select one of the following create stoplist options:  
  
    -   **Create an empty stoplist**  
  
    -   **Create from the system stoplist**  
  
    -   **Create from an existing full-text stoplist**  
  
     For more information, see [New Full-Text Stoplist (General Page)](../../Topics/TopicNameNotContainA/New-Full-Text-Stoplist--General-Page-.md).  
  
8.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
 **To drop a stoplist**  
  
-   [DROP FULLTEXT STOPLIST (Transact-SQL)](assetId:///3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15)  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="queries"></a> Using a Stoplist in Full-Text Queries  
 To make use of a stoplist in queries, you must associate it with a full-text index. You can attach a stoplist to a full-text index when you create the index, or you can alter the index later to add a stoplist.  
  
 **To create a full-text index and associate a stoplist with it**  
  
-   [CREATE FULLTEXT INDEX (Transact-SQL)](assetId:///8b80390f-5f8b-4e66-9bcc-cabd653c19fd)  
  
 **To associate or disassociate a stoplist with an existing full-text index**  
  
-   [ALTER FULLTEXT INDEX (Transact-SQL)](assetId:///b6fbe9e6-3033-4d1b-b6bf-1437baeefec3)  
  
 **To suppress an error message if stopwords cause a Boolean operation on a full-text query to fail**  
  
-   [transform noise words Server Configuration Option](../../Topics/TopicNameNotContainA/transform-noise-words-Server-Configuration-Option.md)  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="viewing"></a> Viewing Stoplists and Stoplist Metadata  
 **To view all the stopwords of a stoplist**  
  
-   [sys.fulltext_stopwords](assetId:///79787bb7-d729-448e-b56a-0a467bbb304f)  
  
 **To get information about all the stoplists in the current database**  
  
-   [sys.fulltext_stoplists](assetId:///eb69fb8f-f6d9-446e-83c0-67afd05dfba0)  
  
-   [sys.fulltext_stopwords](assetId:///79787bb7-d729-448e-b56a-0a467bbb304f)  
  
 **To view the tokenization result of a word breaker, thesaurus, and stoplist combination**  
  
-   [sys.dm_fts_parser](assetId:///2736d376-fb9d-4b28-93ef-472b7a27623a)  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="change"></a> Changing the Stopwords in a Stoplist  
 **To add or drop stopwords from a stoplist**  
  
-   [ALTER FULLTEXT STOPLIST (Transact-SQL)](assetId:///f6ad87d5-6a34-435a-8456-8244947c5c83)  
  
#### To change the stopwords in a stoplist in Management Studio  
  
1.  In Object Explorer, expand the server.  
  
2.  Expand **Databases**, and then expand the database.  
  
3.  Expand **Storage**, and then select **Full Text Stoplists**.  
  
4.  Right-click the stoplist whose properties you want to change, and select **Properties**.  
  
5.  In the [Full-Text Stoplist Properties](../../Topics/TopicNameNotContainA/Full-Text-Stoplist-Properties.md) dialog box:  
  
    1.  In the **Action** list box, select one of the following actions: **Add stopword**, **Delete stopword**, **Delete all stopwords**, or **Clear stoplist**.  
  
    2.  If the **Stopword** text box is enabled for the selected action, enter a single stopword. This stopword must be unique; that is, not yet in this stoplist for the language that you select.  
  
    3.  If the **Full-text language** list box is enabled for the selected action, select a language.  
  
6.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="upgrade"></a> Upgrading Noise Words from SQL Server 2005  
 [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] noise words have been replaced by stopwords. When a database is upgraded from [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], the noise-word files are no longer used. However, the noise-word files are stored in the FTDATA\ FTNoiseThesaurusBak folder, and you can use them later when updating or building the corresponding stoplists. For information about upgrading noise-word files to stoplists, see [Upgrade Full-Text Search](../../Topics/TopicNameNotContainA/Upgrade-Full-Text-Search.md).  
  
 [&#91;TOP&#93;](#TOP)