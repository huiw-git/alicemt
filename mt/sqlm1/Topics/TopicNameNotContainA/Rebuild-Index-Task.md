---
title: Rebuild Index Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
---
# Rebuild Index Task
  The Rebuild Index task rebuilds indexes in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database tables and views. For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../Topics\TopicNameNotContainA/Reorganize-and-Rebuild-Indexes.md).  
  
 By using the Rebuild Index task, a package can rebuild indexes in a single database or multiple databases. If the task rebuilds only the indexes in a single database, you can choose the views and tables whose indexes the task rebuilds.  
  
 This task encapsulates an ALTER INDEX REBUILD statement with the following index rebuild options:  
  
-   Specify a FILLFACTOR percentage or use the original FILLFACTOR amount.  
  
-   Set SORT\_IN\_TEMPDB \= ON to store the intermediate sort result used to rebuild the index in tempdb. When the intermediate sort result is set to OFF, the result is stored in the same database as the index.  
  
-   Set PAD\_INDEX \= ON to allocate the free space specified by FILLFACTOR to the intermediate\-level pages of the index.  
  
-   Set IGNORE\_DUP\_KEY \= ON to allow a multirow insert operation that includes records that violate unique constraints to insert the records that do not violate the unique constraints.  
  
-   Set ONLINE \= ON to not hold table locks so that queries or updates to the underlying table can proceed during re\-indexing.  
  
    > [!NOTE]  
    >  Online index operations are not available in every edition of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
-   Specify a value for MAXDOP to limit the number of processors used in a parallel plan execution.  
  
-   Specify WAIT\_AT\_LOW\_PRIORITY, MAX\_DURATION, and ABORT\_AFTER\_WAIT to control how long the index operation waits for low priority locks.  
  
 For more information about the ALTER INDEX statement and index rebuild options, see [ALTER INDEX &#40;Transact-SQL&#41;](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md).  
  
> [!IMPORTANT]  
>  The time the task takes to create the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement that the task runs is proportionate to the number of indexes the task rebuilds. If the task is configured to rebuild indexes in all the tables and views in a database with a large number of indexes, or to rebuild indexes in multiple databases, the task can take a considerable amount of time to generate the Transact\-SQL statement.  
  
## Configuration of the Rebuild Index Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
 [Rebuild Index Task &#40;Maintenance Plan&#41;](../Topic/Rebuild%20Index%20Task%20\(Maintenance%20Plan\).md)  
  
## Related Tasks  
 For more about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md).  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  