---
title: Add or Remove an Integration Services Project in a Solution
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
---
# Add or Remove an Integration Services Project in a Solution
  The following procedures descibe how to add or remove an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project in a solution.  
  
 You can only add a project to an existing solution, or remove a project from a solution, when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. If you have selected the **Always show solution** option in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)], [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] will display a solution even when that solution contains only one project. Otherwise, [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] will display a solution only when that solution contains more than one project. The additional projects can be either [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] projects or projects of other types.  
  
## Adding an Integration Services Project  
 When you add a project, you can have [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] create a new, blank project, or you can add a project that you have already created for a different solution. You can only add a project to an existing solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
#### To add a new Integration Services project to a solution  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the solution to which you want to add a new [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project, and do one of the following:  
  
    -   Right\-click the solution, click **Add**, and then click **New Project**.  
  
    -   On the **File** menu, point to **Add**, and then click **New Project**.  
  
2.  In the **Add New Project** dialog box, click **Integration Services Project** in the **Templates** pane.  
  
3.  Optionally, edit the project name and location.  
  
4.  Click **OK**.  
  
#### To add an existing Integration Services project to a solution  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the solution to which you want to add an existing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project, and do one of the following:  
  
    -   Right\-click the solution, point to **Add**, and then click **Existing Project**.  
  
    -   On the **File** menu, click **Add**, and then click **Existing Project**.  
  
2.  In the **Add Existing Project** dialog box, browse to locate the project you want to add, and then click **Open**.  
  
3.  The project is added to the solution folder in **Solution Explorer**.  
  
## Removing an Integration Services Project  
 You can only remove a project from a solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. After the solution is visible, you can remove all except one project. As soon as only one project remains, [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] no longer displays the solution folder and you cannot remove the last project.  
  
#### To remove an Integration Services project from a solution  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the solution from which you want to remove an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project.  
  
2.  In Solution Explorer, right\-click the project, and then click **Unload Project**.  
  
3.  Click **OK** to confirm the removal.  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Projects](../Topic/Integration%20Services%20\(SSIS\)%20Projects.md)   
 [Create a New Integration Services Project](../../Topics\TopicNameContainA/Create-a-New-Integration-Services-Project.md)  
  
  