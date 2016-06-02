---
title: MDX Scripting Fundamentals (Analysis Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
---
# MDX Scripting Fundamentals (Analysis Services)
  In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], a Multidimensional Expressions \(MDX\) script is made up of one or more MDX expressions or statements that populate a cube with calculations.  
  
 An MDX script defines the calculation process for a cube. An MDX script is also considered part of the cube itself. Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.  
  
 To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. For more information, see [Define Assignments and Other Script Commands](../../Topics\TopicNameNotContainA/Define-Assignments-and-Other-Script-Commands.md) and [Introduction to MDX Scripting in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892).  
  
 For performance issues related to MDX queries and calculations, see the MDX optimization section in the [SQL Server Analysis Services Performance Guide](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[The Basic MDX Script &#40;MDX&#41;](../Topic/The%20Basic%20MDX%20Script%20\(MDX\).md)|Details the basic MDX script, including the default MDX script provided in each cube, and how MDX scripts generally function within a cube in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].|  
|[Managing Scope and Context &#40;MDX&#41;](../Topic/Managing%20Scope%20and%20Context%20\(MDX\).md)|Describes how to use the [CALCULATE](../Topic/CALCULATE%20Statement%20\(MDX\).md) statement, the [SCOPE](../Topic/SCOPE%20Statement%20\(MDX\).md) statement, and the [This](../Topic/This%20\(MDX\).md) function to manage context and scope within an MDX script.|  
|[Using Variables and Parameters &#40;MDX&#41;](../Topic/Using%20Variables%20and%20Parameters%20\(MDX\).md)|Describes how to use variables and parameters in an MDX script.|  
|[Error Handling &#40;MDX&#41;](../Topic/Error%20Handling%20\(MDX\).md)|Explains error handling within an MDX script.|  
|[Supported MDX &#40;MDX&#41;](../Topic/Supported%20MDX%20\(MDX\).md)|Provides a list of supported MDX operators, statements, and functions within an MDX script.|  
  
## See Also  
 [MDX Language Reference &#40;MDX&#41;](../Topic/MDX%20Language%20Reference%20\(MDX\).md)  
  
  