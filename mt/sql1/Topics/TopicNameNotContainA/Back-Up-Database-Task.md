---
title: "Back Up Database Task"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
caps.latest.revision: 47
caps.handback.revision: 0
manager: jhubbard
---
# Back Up Database Task
The Back Up Database task performs different types of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database backups. For more information, see [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md).  
  
 By using the Back Up Database task, a package can back up a single database or multiple databases. If the task backs up only a single database, you can choose the backup component: the database, or its files and filegroups.  
  
## Supported Recover Models and Backup Types  
 The following table lists the recovery models and backup types that the Back Up Database task supports.  
  
|Recovery model|Database|Database differential|Transaction log|File or file differential|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Simple|Required|Optional|Not supported|Not supported|  
|Full|Required|Optional|Required|Optional|  
|Bulk-logged|Required|Optional|Required|Optional|  
  
 The Back Up Database task encapsulates a Transact-SQL BACKUP statement. For more information, see [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1).  
  
## Configuration of the Back Up Database Task  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Back Up Database Task (Maintenance Plan)](../../Topics/TopicNameNotContainA/Back-Up-Database-Task--Maintenance-Plan-.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)