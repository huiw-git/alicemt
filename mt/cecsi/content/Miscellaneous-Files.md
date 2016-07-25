---
title: "Miscellaneous Files"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
caps.latest.revision: 5
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
# Miscellaneous Files
Files that that are external to any project are called *miscellaneous files*. When you have a solution open, you can open and modify miscellaneous files related to the project. A file is classified as a miscellaneous file if the file extension is not associated with the project code editor. For example, in a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Scripts Project, files with the extension .txt or .mdx will be treated as miscellaneous files. In an MDX project, files with the extension of .txt or .sql will be treated as miscellaneous files. To associate a file extension with a code editor, see [How to: Associate File Extensions to a Code Editor](assetId:///193630f4-93de-4950-8f36-68702531f925).  
  
There are a number of reasons why it is useful to be able to add miscellaneous files to your project. You might have a file that is not necessarily a recognized script but integral to the solution's development. Common examples include development notes or instructions, data files, and code clips.  
  
Miscellaneous files provide flexibility. For example, suppose you have a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Scripts Project that has several scripts for creation of tables and stored procedures in your database. You also have several data files for the tables with file extensions .BCP and execution instructions in a README.TXT file. You can attach the data and the README files as miscellaneous files to the project to take advantage of source control and other features of the project system.  
  
[!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] menus and toolbars change according to the format of the file you open. When you open a text file, for example, the Text Editor toolbar appears. If you open an XML Schema file, the XML Schema toolbar appears. While editing your XML Schema, the Text Editor toolbar is unavailable. When you switch between a project file and a miscellaneous file, all project-related commands and toolbars are replaced by those relevant to the miscellaneous file.  
  
## See Also  
[Files That Manage Solutions and Projects](../content/Files-That-Manage-Solutions-and-Projects.md)  
[Solutions &#40;SQL Server Management Studio&#41;](../content/Solutions--SQL-Server-Management-Studio-.md)  
[Projects &#40;SQL Server Management Studio&#41;](../content/Projects--SQL-Server-Management-Studio-.md)  
  
