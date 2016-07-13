---
title: Add New Items to a Project
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
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
# Add New Items to a Project
Add new items to a project to extend application functionality. A new item can be a query or a connection. [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] has two project types: [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Script Project, and Analysis Services Script Project. The project type determines the items that you can add to the project. For example, you can add a [!INCLUDE[tsql](../content/includes/tsql_md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Script project, but you cannot add it to an Analysis Services Script Project.  
  
[!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] does not allow you to create folders within projects. To organize your work, create multiple projects within the solution.  
  
### To add a new query to an existing project  
  
1.  In Solution Explorer, select a target project.  
  
2.  On the **Project** menu, click **Add New Item**.  
  
3.  In the **Add New Item** dialog box, select a category in the left pane.  
  
4.  Select a query template in the right pane, and then click **Add**. The new query is added in the **Queries** folder of the project.  
  
5.  In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**. You can click **Cancel** on the connection dialog if you do not want to associate a connection to the new query.  
  
6.  Rename the query in Solution Explorer if you wish.  
  
### To add a new connection to an existing project  
  
1.  In Solution Explorer, select a target project.  
  
2.  On the **Project** menu, click **Add New Item**.  
  
3.  Select **Connection** in the left pane.  
  
4.  Select **New Connection** in the right pane, and then click **Add**.  
  
5.  In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**. The new connection gets added in the **Connections** folder of the project.  
  
## See Also  
[Solution Explorer](../content/Solution-Explorer.md)  
[Associating File Extensions to a Code Editor](assetId:///193630f4-93de-4950-8f36-68702531f925)  
[Add Existing Items to a Project](../content/Add-Existing-Items-to-a-Project.md)  
[Remove or Delete an Item or Project](../content/Remove-or-Delete-an-Item-or-Project.md)  
  
