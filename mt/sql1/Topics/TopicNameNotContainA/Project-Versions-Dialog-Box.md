---
title: "Project Versions Dialog Box"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Project Versions Dialog Box
Use the **Project Versions** dialog box to view versions of a project and to restore a previous version.  
  
 You can also view previous versions in the [catalog.object_versions (SSISDB Database)](assetId:///2fd8c020-1c77-4702-8e6b-efa6a348daab) view, and use the [catalog.restore_project (SSISDB Database)](assetId:///8adee525-579b-4d2f-b807-e2ecc07fb2e9) stored procedure to restore previous versions.  
  
 **What do you want to do?**  
  
-   [Open the Project Versions dialog box](#open_dialog)  
  
-   [Restore a Project Version](#restore)  
  
##  <a name="open_dialog"></a> Open the Project Versions dialog box  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], connect to the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] server.  
  
     That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] that hosts the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] database.  
  
2.  In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.  
  
3.  Expand the **Integration Services Catalogs** node to display the **SSISDB** node.  
  
4.  The **SSISDB** node contains one or more folders that each contain one or more projects. Expand the folder that contains the project you are interested in.  
  
5.  Right-click the project, and then click **Versions**.  
  
 In the **Project Versions** dialog box, the **Versions** table displays the list of versions of the project that have been deployed on the server, with the date and time the version was deployed, the date and time the version was restored (if it was restored), the version description, and a version identifier. The currently active version is indicated with a check mark in the **Current** column of the table.  
  
##  <a name="restore"></a> Restore a Project Version  
 To restore a previous version of a project, select the version in the **Versions** table, and then click **Restore to Selected Version**. The project is restored to the selected version and that version is indicated with a check mark in the **Current** column of the **Versions** table.