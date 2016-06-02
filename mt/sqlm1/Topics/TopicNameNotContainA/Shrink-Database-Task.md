---
title: Shrink Database Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
---
# Shrink Database Task
  The Shrink Database task reduces the size of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database data and log files.  
  
 By using the Shrink Database task, a package can shrink files for a single database or multiple databases.  
  
 Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file. When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.  
  
> [!WARNING]  
>  Data that is moved to shrink a file can be scattered to any available location in the file. This causes index fragmentation and can slow the performance of queries that search a range of the index. To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.  
  
## Commands  
 The Shrink Database task encapsulates a DBCC SHRINKDATABASE command, including the following arguments and options:  
  
-   *database\_name*  
  
-   *target\_percent*  
  
-   NOTRUNCATE or TRUNCATEONLY.  
  
 If the Shrink Database task shrinks multiple databases, the task runs multiple SHRINKDATABASE commands, one for each database. All instances of the SHRINKDATABASE command use the same argument values, except for the *database\_name* argument. For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../Topic/DBCC%20SHRINKDATABASE%20\(Transact-SQL\).md).  
  
## Configuration of the Shrink Database Task  
 You can set properties through the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Shrink Database Task &#40;Maintenance Plan&#41;](../Topic/Shrink%20Database%20Task%20\(Maintenance%20Plan\).md)  
  
 For more information about setting these properties in the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
  