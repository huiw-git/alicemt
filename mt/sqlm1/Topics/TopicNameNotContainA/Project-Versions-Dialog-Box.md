---
title: Project Versions Dialog Box
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
---
# Project Versions Dialog Box
  Use the **Project Versions** dialog box to view versions of a project and to restore a previous version.  
  
 You can also view previous versions in the [catalog.object_versions &#40;SSISDB Database&#41;](../Topic/catalog.object_versions%20\(SSISDB%20Database\).md) view, and use the [catalog.restore_project &#40;SSISDB Database&#41;](../Topic/catalog.restore_project%20\(SSISDB%20Database\).md) stored procedure to restore previous versions.  
  
 **What do you want to do?**  
  
-   [Open the Project Versions dialog box](#open_dialog)  
  
-   [Restore a Project Version](#restore)  
  
##  <a name="open_dialog"></a> Open the Project Versions dialog box  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server.  
  
     That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] that hosts the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] database.  
  
2.  In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.  
  
3.  Expand the **Integration Services Catalogs** node to display the **SSISDB** node.  
  
4.  The **SSISDB** node contains one or more folders that each contain one or more projects. Expand the folder that contains the project you are interested in.  
  
5.  Right\-click the project, and then click **Versions**.  
  
 In the **Project Versions** dialog box, the **Versions** table displays the list of versions of the project that have been deployed on the server, with the date and time the version was deployed, the date and time the version was restored \(if it was restored\), the version description, and a version identifier. The currently active version is indicated with a check mark in the **Current** column of the table.  
  
##  <a name="restore"></a> Restore a Project Version  
 To restore a previous version of a project, select the version in the **Versions** table, and then click **Restore to Selected Version**. The project is restored to the selected version and that version is indicated with a check mark in the **Current** column of the **Versions** table.  
  
  