---
title: Update Statistics Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
---
# Update Statistics Task
  The Update Statistics task updates information about the distribution of key values for one or more statistics groups \(collections\) in the specified table or indexed view. For more information, see [Statistics](../../Topics\TopicNameNotContainA/Statistics.md).  
  
 By using the Update Statistics task, a package can update statistics for a single database or multiple databases. If the task updates only the statistics in a single database, you can choose the views or the tables whose statistics the task updates. You can configure the update to update all statistics, column statistics only, or index statistics only.  
  
 This task encapsulates an UPDATE STATISTICS statement, including the following arguments and clauses:  
  
-   The *table\_name* or *view\_name* argument.  
  
-   If the update applies to all statistics, the WITH ALL clause is implied.  
  
-   If the update applies only to columns, the WITH COLUMN clause is included.  
  
-   If the update applies only to indexes, the WITH INDEX clause is included.  
  
 If the Update Statistics task updates statistics in multiple databases, the task runs multiple UPDATE STATISTICS statements, one for each table or view. All instances of UPDATE STATISTICS use the same clause, but different *table\_name* or *view\_name* values. For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](../Topic/CREATE%20STATISTICS%20\(Transact-SQL\).md) and [UPDATE STATISTICS &#40;Transact-SQL&#41;](../Topic/UPDATE%20STATISTICS%20\(Transact-SQL\).md).  
  
> [!IMPORTANT]  
>  The time the task takes to create the Transact\-SQL statement that the task runs is proportionate to the number of statistics the task updates. If the task is configured to update statistics in all the tables and views in a database with a large number of indexes, or to update statistics in multiple databases, the task can take a considerable amount of time to generate the Transact\-SQL statement.  
  
## Configuration of the Update Statistics Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Update Statistics Task &#40;Maintenance Plan&#41;](../Topic/Update%20Statistics%20Task%20\(Maintenance%20Plan\).md)  
  
## Related Tasks  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  