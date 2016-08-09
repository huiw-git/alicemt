---
title: "Execute T-SQL Statement Task"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# Execute T-SQL Statement Task
The Execute T-SQL Statement task runs Transact-SQL statements. For more information, see [Transact-SQL Reference (Transact-SQL)](assetId:///dbba47d7-e08e-4435-b876-35dced1f325d) and [Integration Services (SSIS) Queries](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Queries.md).  
  
 This task is similar to the Execute SQL task. However, the Execute T-SQL Statement task supports only the Transact-SQL version of the SQL language and you cannot use this task to run statements on servers that use other dialects of the SQL language. If you need to run parameterized queries, save the query results to variables, or use property expressions, you should use the Execute SQL task instead of the Execute T-SQL Statement task. For more information, see [Execute SQL Task](../../Topics/TopicNameNotContainA/Execute-SQL-Task.md).  
  
## Configuration of the Execute T-SQL Task  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Execute T-SQL Statement Task (Maintenance Plan)](../../Topics/TopicNameNotContainA/Execute-T-SQL-Statement-Task--Maintenance-Plan-.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## See Also  
 [Integration Services Tasks](../../Topics/TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics/TopicNameNotContainA/Control-Flow.md)   
 [MERGE in Integration Services Packages](../../Topics/TopicNameNotContainA/MERGE-in-Integration-Services-Packages.md)