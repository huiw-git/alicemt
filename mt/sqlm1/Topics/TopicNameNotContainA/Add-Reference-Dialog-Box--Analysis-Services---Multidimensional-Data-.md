---
title: Add Reference Dialog Box (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 457958c4-6baa-474d-99a0-34c195ceba09
---
# Add Reference Dialog Box (Analysis Services - Multidimensional Data)
  Use the **Add Reference** dialog box in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to add a reference to a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] .NET Framework assembly or to another project to your development project. You can display the **Add Reference** dialog box by right\-clicking the **Assemblies** folder of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project in **Solution Explorer** and selecting **New Assembly Reference** from the context menu.  
  
## Options  
  
|Term|Definition|  
|----------|----------------|  
|**.NET**|Select this tab to add a reference to a registered component. This tab displays a grid that contains a list of registered .NET Framework components. Select one or more items from the grid, and then click **Add** to add the selected .NET components to **Selected products and components**. The grid contains the following columns:<br /><br /> **Component name**: The full, or "friendly," name of the component. Select the title to sort by the component name.<br /><br /> **Version**:<br />                      The listed version number of the component. Select the title to sort by the version.<br /><br /> **Runtime**:<br />                      The version of the .NET Framework on which the component is based. Select the title to sort by the runtime version.<br /><br /> **Path**:<br />                      The file name of the component and the path where it is located. Select the title to sort by the path.|  
|**Browse**|Click to browse the file system for an assembly not listed in the **.NET** or **Recent** tabs. This tab displays the following options:<br /><br /> **Look in**:<br />                      Select a folder from this drop\-down list. Selecting a folder from this list displays the contents of the folder in the primary pane.<br /><br /> **Go to last folder visited**:<br />                      Returns **Look in** to the previous location.<br /><br /> **Up One Level**:<br />                      Locates the next higher folder in the hierarchy.<br /><br /> **Create New Folder**:<br />                      Select to create a new child folder under the folder selected in **Look in**.<br /><br /> **View Menu**:<br />                      Select to change the view of contents in the primary pane. The following options are available: **Thumbnails**, **Tiles**, **Icons**, **List**, **Details**. For more information about the options in **View Menu**, see the "Viewing files and folders overview" topic in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows documentation.|  
|**Recent**|Displays a list of component references recently added to projects in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. Select one or more items from the grid, and then click **Add** to add the selected .NET Framework assemblies to **Selected products and components**. The grid contains the following columns:<br /><br /> **Component name**:<br />                      The full, or "friendly," name of the component. Select the title to sort by the component name.<br /><br /> **Version**:<br />                      The listed version number of the component. Select the title to sort by the version.<br /><br /> **Runtime**:<br />                      The version of the .NET Framework on which the component is based. Select the title to sort by the runtime version.<br /><br /> **Path**:<br />                      The file name of the component and the path where it is located. Select the title to sort by the path.|  
|**Add**|Click to add a component selected in the **.NET**, **Browse**, or **Recent** tabs to **Selected projects and components**.|  
|**Remove**|Click to remove a component selected in **Selected projects and components**.|  
|**Selected projects and components**|Displays a list of component references to be added to the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. Select one or more items from the grid, and then click **Remove** to remove the selected components from the grid. The grid contains the following columns:<br /><br /> **Component name**:<br />                      The full, or "friendly," name of the component. Select the title to sort by the component name.<br /><br /> **Version**:<br />                      The listed version number of the component. Select the title to sort by the version.<br /><br /> **Runtime**:<br />                      The version of the .NET Framework on which the component is based. Select the title to sort by the runtime version.<br /><br /> **Path**:<br />                      The file name of the component and the path where it is located. Select the title to sort by the path.|  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)   
 [Multidimensional Model Assemblies Management](../../Topics\TopicNameNotContainA/Multidimensional-Model-Assemblies-Management.md)  
  
  