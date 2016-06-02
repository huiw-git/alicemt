---
title: Reorganize Index Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
---
# Reorganize Index Task
  The Reorganize Index task reorganizes indexes in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database tables and views. For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../Topics\TopicNameNotContainA/Reorganize-and-Rebuild-Indexes.md).  
  
 By using the Reorganize Index task, a package can reorganize indexes in a single database or multiple databases. If the task reorganizes only the indexes in a single database, you can choose the views or the tables whose indexes the task reorganizes. The Reorganize Index task also includes an option to compact large object data. Large object data is data with the **image**, **text**, **ntext**, **varchar\(max\)**, **nvarchar\(max\)**, **varbinary\(max\)**, or **xml** data type. For more information, see [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md).  
  
 The Reorganize Index task encapsulates the Transact\-SQL ALTER INDEX statement. If you choose to compact large object data, the statement uses the REORGANIZE WITH \(LOB\_COMPACTION \= ON\) clause, otherwise LOB\_COMPACTION is set to OFF. For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md).  
  
> [!IMPORTANT]  
>  The time the task takes to create the Transact\-SQL statement that the task runs is proportionate to the number of indexes the task reorganizes. If the task is configured to reorganize indexes in all the tables and views in a database that holds a large number of indexes, or to reorganize indexes in multiple databases, the task can take a considerable amount of time to generate the Transact\-SQL statement.  
  
## Configuration of the Reorganize Index Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Reorganize Index Task &#40;Maintenance Plan&#41;](../Topic/Reorganize%20Index%20Task%20\(Maintenance%20Plan\).md)  
  
## Related Tasks  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md).  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  