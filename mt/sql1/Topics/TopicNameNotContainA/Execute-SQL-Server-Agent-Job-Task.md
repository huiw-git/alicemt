---
title: "Execute SQL Server Agent Job Task"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
caps.latest.revision: 45
caps.handback.revision: 0
manager: jhubbard
---
# Execute SQL Server Agent Job Task
The Execute [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent Job task runs [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent jobs. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent is a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows service that runs jobs that have been defined in an instance of SQL Server. You can create jobs that execute Transact-SQL statements and ActiveX scripts, perform [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] and Replication maintenance tasks, or run packages. You can also configure a job to monitor [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and fire alerts. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent jobs are typically used to automate tasks that you perform repeatedly. For more information, see [Implementing Jobs](assetId:///69e06724-25c7-4fb3-8a5b-3d4596f21756).  
  
 By using the Execute [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent Job task, a package can perform administrative tasks related to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] components. For example, a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent job can run a system stored procedure such as **sp_enum_dtspackages** to obtain a list of packages in a folder.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent must be running before local or multiserver administrative jobs can run automatically.  
  
 This task encapsulates the **sp_start_job** system procedure and passes the name of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent job to the procedure as an argument. For more information, see [sp_start_job (Transact-SQL)](assetId:///8a91df6a-eb84-4512-9a17-4a6e32a9538a).  
  
## Configuring the Execute SQL Server Agent Job Task  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Execute SQL Server Agent Job Task (Maintenance Plan)](../../Topics/TopicNameNotContainA/Execute-SQL-Server-Agent-Job-Task--Maintenance-Plan-.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)