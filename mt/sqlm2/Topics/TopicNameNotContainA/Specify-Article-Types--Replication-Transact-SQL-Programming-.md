---
title: Specify Article Types (Replication Transact-SQL Programming)
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
---
# Specify Article Types (Replication Transact-SQL Programming)
  The default article types for replication are table articles, but you can publish other database objects as articles, including views, stored procedures, user\-defined functions, and stored procedure execution. You can use replication stored procedures to specify an article type programmatically when you define an article. The procedures that you use depend on the type of replication and article type.  
  
> [!NOTE]  
>  The schema\-only designation when defining table, view, and stored procedure articles indicates that only the object definition is replicated.  
  
### To publish a table article in a transactional or snapshot publication  
  
1.  At the Publisher on the publication database, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). Specify one of the following values for **@type** to define the type of article:  
  
    -   **logbased** \- a log\-based table article, which is the default for transactional and snapshot replication. Replication automatically generates the stored procedure used for horizontal filtering and the view that defines a vertically filtered article.  
  
    -   **logbased manualfilter** \- a log\-based, horizontally filtered article where the stored procedure used for horizontal filtering is manually created and defined by the user and specified for **@filter**. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
    -   **logbased manualview** \- a log\-based, vertically filtered article where the view that defines the vertically filtered article is created and defined by the user and specified for **@sync\_object**. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md) and [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
    -   **logbased manualboth** \- a log\-based, horizontally and vertically filtered article where both the stored procedure used for horizontal filtering and the view that defines the vertically filtered article are created and defined by the user and specified for **@filter** and **@sync\_object**, respectively. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md) and [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
     This defines a new article for the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
2.  For **logbased manualboth** and **logbased manualfilter** articles, execute [sp\_articlefilter](../Topic/sp_articlefilter%20\(Transact-SQL\).md) to generate the filtering stored procedure for a horizontally filtered article. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
3.  For **logbased manualboth**, **logbased manualview**, and **logbased manualfilter** articles, execute [sp\_articleview](../Topic/sp_articleview%20\(Transact-SQL\).md) to generate the view that defines the vertically filtered article. For more information, see [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
### To publish a view or indexed view article in a transactional or snapshot publication  
  
1.  At the Publisher on the publication database, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). Specify one of the following values for **@type** to define the type of article:  
  
    -   **indexed view logbased** \- a log\-based indexed view article. Replication automatically generates the stored procedure used for horizontal filtering and the view that defines a vertically filtered article.  
  
    -   **view schema only** \- a schema\-only view article. The base table must also be replicated.  
  
    -   **indexed view schema only** \- a schema\-only indexed view article. The base table must also be replicated.  
  
    -   **indexed view logbased manualfilter** \- a log\-based, horizontally filtered indexed view article where the stored procedure used for horizontal filtering is manually created and defined by the user and specified for **@filter**. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
    -   **indexed view logbased manualview** \- a log\-based, filtered indexed view article where the view that defines a vertically filtered article is created and defined by the user and specified for **@sync\_object**. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md) and [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
    -   **indexed view logbased manualboth** \- a log\-based, filtered indexed view article where both the stored procedure used for horizontal filtering and the view that defines a vertically filtered article are created and defined by the user and specified for **@filter** and **@sync\_object**, respectively. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md) and [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
     This defines a new article for the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
2.  For **logbased manualboth** and **logbased manualfilter** articles, execute [sp\_articlefilter](../Topic/sp_articlefilter%20\(Transact-SQL\).md) to generate the filtering stored procedure for a horizontally filtered article. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
3.  For **logbased manualboth**, **logbased manualview**, and **logbased manualfilter** articles, execute [sp\_articleview](../Topic/sp_articleview%20\(Transact-SQL\).md) to generate the view that defines the vertically filtered article. For more information, see [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
### To publish a stored procedure, stored procedure execution, or user\-defined function article in a transactional or snapshot publication  
  
1.  At the Publisher on the publication database, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). Specify one of the following values for **@type** to define the type of article:  
  
    -   **proc schema only** \- a schema\-only stored procedure article.  
  
    -   **proc exec** \- replicates the execution of the stored procedure to all Subscribers of the article. For more information, see [Publishing Stored Procedure Execution in Transactional Replication](../../Topics\TopicNameNotContainA/Publishing-Stored-Procedure-Execution-in-Transactional-Replication.md).  
  
    -   **serializable proc exec** \- replicates the execution of the stored procedure only if it is executed within the context of a serializable transaction. For more information, see [Publishing Stored Procedure Execution in Transactional Replication](../../Topics\TopicNameNotContainA/Publishing-Stored-Procedure-Execution-in-Transactional-Replication.md).  
  
    -   **func schema only** \- a schema\-only user\-defined function article.  
  
     This defines a new article for the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
### To publish a table or view article in a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify one of the following values for **@type** to define the type of article:  
  
    -   **table** \- a table article.  
  
    -   **indexed view schema only** \- a schema\-only indexed view article.  
  
    -   **view schema only** \- a schema\-only view article.  
  
     This defines a new article for the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
### To publish a stored procedure or user\-defined function article in a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify one of the following values for **@type** to define the type of article:  
  
    -   **func schema only** \- a schema\-only user\-defined function article.  
  
    -   **proc schema only** \- a schema\-only stored procedure article.  
  
     This defines a new article for the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
## See Also  
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)  
  
  