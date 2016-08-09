---
title: "Package Properties Dialog Box"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Package Properties Dialog Box
Use the **Package Properties** dialog box to view properties for packages that are stored on the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] server.  
  
 For more information, see [Integration Services (SSIS) Server](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Server.md).  
  
 **What do you want to do?**  
  
-   [Open the Package Properties dialog box](#open_dialog)  
  
-   [Configure the Options](#options)  
  
##  <a name="open_dialog"></a> Open the Package Properties dialog box  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], connect to the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] server.  
  
     You’re connecting to the instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] that hosts the SSISDB database.  
  
2.  In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.  
  
3.  Expand the **SSISDB** node.  
  
4.  Expand the folder that contains the package you want to view properties for.  
  
5.  Right-click the package, and then select **Properties**.  
  
##  <a name="options"></a> Configure the Options  
 Use the **General** page to view the properties of the selected package.  
  
 All properties on the **General** page are read-only.  
  
 **Name**  
 Displays the name of the package.  
  
 **Identifier**  
 Lists the package ID.  
  
 **Entry Point**  
 The value of **True** indicates that the package is started directly. The value of **False** indicates that the package is started by another package using the Execute Package task. The default value is **True**.  
  
 You set this property in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] for both the parent package and the child packages by right-clicking the package in Solution Explorer and then clicking **Entry-point Package**.  
  
 **Description**  
 Displays the optional description of the package.