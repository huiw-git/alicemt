---
title: View Package Objects
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
---
# View Package Objects
  In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, the **Package Explorer** tab provides an explorer view of the package. The view reflects the container hierarchy of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] architecture. The package container is at the top of the hierarchy, and you expand the package to view the connections, executables, event handlers, log providers, precedence constraints, and variables in the package.  
  
 The executables, which are the containers and tasks in the package, can include event handlers, precedence constraints, and variables. [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] supports a nested hierarchy of containers, and the For Loop, Foreach Loop, and Sequence containers can include other executables.  
  
 If a package includes a data flow, the **Package Explorer** lists the Data Flow task and includes a **Components** folder that lists the data flow components.  
  
 From the **Package Explorer** tab, you can delete objects in a package and access the **Properties** window to view object properties.  
  
 The following diagram shows a tree view of a simple package.  
  
 ![Screenshot of the Package Explorer tab](../../Images\Image\ImageNotContaina/PackageExplorer.gif "PackageExplorer")  
  
### To view package content  
  
-   [View Package Objects in Package Explorer](../../Topics\TopicNameNotContainA/View-Package-Objects-in-Package-Explorer.md)  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Integration Services Containers](../../Topics\TopicNameNotContainA/Integration-Services-Containers.md)   
 [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md)   
 [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md)   
 [Integration Services &#40;SSIS&#41; Event Handlers](../Topic/Integration%20Services%20\(SSIS\)%20Event%20Handlers.md)   
 [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md)  
  
  