---
title: "Reorganize Index Task"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
caps.latest.revision: 44
caps.handback.revision: 0
manager: jhubbard
---
# Reorganize Index Task
The Reorganize Index task reorganizes indexes in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database tables and views. For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../Topics/TopicNameNotContainA/Reorganize-and-Rebuild-Indexes.md).  
  
 By using the Reorganize Index task, a package can reorganize indexes in a single database or multiple databases. If the task reorganizes only the indexes in a single database, you can choose the views or the tables whose indexes the task reorganizes. The Reorganize Index task also includes an option to compact large object data. Large object data is data with the **image**, **text**, **ntext**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, or **xml** data type. For more information, see [Data Types (Transact-SQL)](assetId:///a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4).  
  
 The Reorganize Index task encapsulates the Transact-SQL ALTER INDEX statement. If you choose to compact large object data, the statement uses the REORGANIZE WITH (LOB_COMPACTION = ON) clause, otherwise LOB_COMPACTION is set to OFF. For more information, see [ALTER INDEX (Transact-SQL)](assetId:///b796c829-ef3a-405c-a784-48286d4fb2b9).  
  
> [!IMPORTANT]  
>  The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of indexes the task reorganizes. If the task is configured to reorganize indexes in all the tables and views in a database that holds a large number of indexes, or to reorganize indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.  
  
## Configuration of the Reorganize Index Task  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer.  
  
 For information about the properties that you can set in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Reorganize Index Task (Maintenance Plan)](../../Topics/TopicNameNotContainA/Reorganize-Index-Task--Maintenance-Plan-.md)  
  
## Related Tasks  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, see [Set the Properties of a Task or Container](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md).  
  
## See Also  
 [Integration Services Tasks](../../Topics/TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics/TopicNameNotContainA/Control-Flow.md)