---
title: Files That Manage Solutions and Projects
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Files That Manage Solutions and Projects
This topic describes the file types that are specific to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]. By default, all solutions and their projects are created in \\My Documents\\SQL Server Management Studio Projects.  
  
## Management Studio Solution Files  
[!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] uses different file types than [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssBIDevStudioFull](../content/includes/ssBIDevStudioFull_md.md)] or [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Visual Studio. This means you cannot open a [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] solution in [!INCLUDE[ssBIDevStudioFull](../content/includes/ssBIDevStudioFull_md.md)] or in Visual Studio. [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] solution files allow Solution Explorer to display a graphical interface for managing your files.  
  
|Extension|File type|Description|Created by|  
|-------------|-------------|---------------|--------------|  
|.ssmssln|[!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] Solution Object|Provides the environment with references to the location on disk of [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] projects, project items, and solution|[!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]|  
  
## Management Studio Project Files  
In the same way that solutions contain solution files that manage objects in a solution, projects contain project files. The type of project file that [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] creates for a project depends on the template used to create the project. The following table describes the type of file created for each project.  
  
|Extension|Project template|  
|-------------|--------------------|  
|.ssmssqlproj|[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Scripts Project|  
|.ssmsasproj|[!INCLUDE[ssASnoversion](../content/includes/ssASnoversion_md.md)] Scripts Project|  
  
## Location of Solution\-Level Files  
By default, solution\-level files are created in the physical directory of the first project that is created with the solution. You can specify a directory for the solution by creating a solution, or you can specify the directory when you create a new project.  
  
If you have a directory structure similar to the logical structure shown in Solution Explorer, project and solution files are easier to locate and share with other developers on a team.  
  
## See Also  
[Manage Files with Encoding](../content/Manage-Files-with-Encoding.md)  
[Miscellaneous Files](../content/Miscellaneous-Files.md)  
[Solution Explorer](../content/Solution-Explorer.md)  
[Solutions &#40;SQL Server Management Studio&#41;](../content/Solutions--SQL-Server-Management-Studio-.md)  
[Projects &#40;SQL Server Management Studio&#41;](../content/Projects--SQL-Server-Management-Studio-.md)  
[Solution Explorer Source Control](https://msdn.microsoft.com/en-us/library/ms173879.aspx)  
  
