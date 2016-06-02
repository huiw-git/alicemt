---
title: Back Up Database Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
---
# Back Up Database Task
  The Back Up Database task performs different types of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database backups. For more information, see [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md).  
  
 By using the Back Up Database task, a package can back up a single database or multiple databases. If the task backs up only a single database, you can choose the backup component: the database, or its files and filegroups.  
  
## Supported Recover Models and Backup Types  
 The following table lists the recovery models and backup types that the Back Up Database task supports.  
  
|Recovery model|Database|Database differential|Transaction log|File or file differential|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Simple|Required|Optional|Not supported|Not supported|  
|Full|Required|Optional|Required|Optional|  
|Bulk\-logged|Required|Optional|Required|Optional|  
  
 The Back Up Database task encapsulates a Transact\-SQL BACKUP statement. For more information, see [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md).  
  
## Configuration of the Back Up Database Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Back Up Database Task &#40;Maintenance Plan&#41;](../Topic/Back%20Up%20Database%20Task%20\(Maintenance%20Plan\).md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
  