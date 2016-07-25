---
title: "Add Existing Items to a Project"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
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
# Add Existing Items to a Project
Add new items to a project to extend application functionality. An existing item can be a query or a miscellaneous file. [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] has two project types: [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Script Project, and Analysis Services Script Project. The project type determines the query files that you can add to the project. For example, you can add a [!INCLUDE[tsql](../content/includes/tsql_md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Script project, but you cannot add it to an Analysis Services Script Project. To associate additional file extensions to a project type, see [How to: Associate File Extensions to a Code Editor](assetId:///193630f4-93de-4950-8f36-68702531f925).  
  
### To add an existing query or a miscellaneous file to a project  
  
1.  In Solution Explorer, select a target project.  
  
2.  On the **Project** menu, click **Add Existing Item**.  
  
    **Look in**  
    Locate the files or folders to add to your project from this list. For XML Web services and ASP.NET Web applications, the files are located on the Web server.  
  
    **Desktop**  
    Displays the files and folders located on the desktop.  
  
    **My Projects**  
    Displays the files and folders at the default **My Projects** location.  
  
    **My Computer**  
    Displays the contents of your **My Computer** folder.  
  
    **File name**  
    Use this option to filter the files and folders that are displayed. Enter the full or partial file name on which to filter; use an asterisk (`*`) as a wildcard.  
  
    > [!NOTE]  
    > Navigate to Web and network locations by entering the URL or network path in the **File name** box. For example, **http://mywebsite** displays the files available at the mywebsite Web location, and **\\\myserver\myshare** displays the files available at the myshare location on myserver.  
  
    **Files of type**  
    Use this option to filter files based on file extension. Each product lists default filters of the most common file types.  
  
    **Add**  
    Use this drop-down button to add the item to the project and open the item in its default editor.  
  
    -   **Add**  
  
        Copies the existing item to your project folder on disk and adds the item under the selected project in Solution Explorer. Any changes made to the item are not reflected in the item at the original location. This is the default editor for the file type.  
  
    -   **Add As Link**  
  
        Adds the selected file to the project and opens it with the default editor for the file type. This option opens the originally selected file and does not copy the file to the project folder.  
  
3.  If you are adding query files, the connection dialog will prompt you to specify a connection for the query. You can click **Cancel** on the connection dialog if you do not want to associate a connection to the query.  
  
4.  The file will be added to the **Queries** or **Miscellaneous Files** folder of the project.  
  
## See Also  
[Solution Explorer](../content/Solution-Explorer.md)  
[Add New Items to a Project](../content/Add-New-Items-to-a-Project.md)  
[Remove or Delete an Item or Project](../content/Remove-or-Delete-an-Item-or-Project.md)  
  
