---
title: Execute SQL Server Agent Job Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
---
# Execute SQL Server Agent Job Task
  The Execute [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent Job task runs [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent jobs. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows service that runs jobs that have been defined in an instance of SQL Server. You can create jobs that execute Transact\-SQL statements and ActiveX scripts, perform [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] and Replication maintenance tasks, or run packages. You can also configure a job to monitor [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and fire alerts. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent jobs are typically used to automate tasks that you perform repeatedly. For more information, see [Implement Jobs](../Topic/Implement%20Jobs.md).  
  
 By using the Execute [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent Job task, a package can perform administrative tasks related to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components. For example, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job can run a system stored procedure such as **sp\_enum\_dtspackages** to obtain a list of packages in a folder.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent must be running before local or multiserver administrative jobs can run automatically.  
  
 This task encapsulates the **sp\_start\_job** system procedure and passes the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job to the procedure as an argument. For more information, see [sp_start_job &#40;Transact-SQL&#41;](../Topic/sp_start_job%20\(Transact-SQL\).md).  
  
## Configuring the Execute SQL Server Agent Job Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Execute SQL Server Agent Job Task &#40;Maintenance Plan&#41;](../Topic/Execute%20SQL%20Server%20Agent%20Job%20Task%20\(Maintenance%20Plan\).md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
  