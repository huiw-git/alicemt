---
title: "Check Database Integrity Task"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
caps.latest.revision: 39
caps.handback.revision: 0
manager: jhubbard
---
# Check Database Integrity Task
The Check Database Integrity task checks the allocation and structural integrity of all the objects in the specified database. The task can check a single database or multiple databases, and you can choose whether to also check the database indexes.  
  
 The Check Database Integrity task encapsulates the DBCC CHECKDB statement. For more information, see [How to: Set Task Properties](assetId:///2c506167-0b69-49f7-9282-241e411910df).  
  
## Configuration of the Check Database Integrity Task  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Check Database Integrity Task (Maintenance Plan)](../../Topics/TopicNameNotContainA/Check-Database-Integrity-Task--Maintenance-Plan-.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)