---
title: "MDX Scripting Fundamentals (Analysis Services)"
ms.custom: na
ms.date: 08/09/2016
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
caps.latest.revision: 35
caps.handback.revision: 0
manager: mblythe
---
# MDX Scripting Fundamentals (Analysis Services)
In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], a Multidimensional Expressions (MDX) script is made up of one or more MDX expressions or statements that populate a cube with calculations.  
  
 An MDX script defines the calculation process for a cube. An MDX script is also considered part of the cube itself. Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.  
  
 To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)]. For more information, see [Define Assignments and Other Script Commands](../../Topics/TopicNameNotContainA/Define-Assignments-and-Other-Script-Commands.md) and [Introduction to MDX Scripting in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892).  
  
 For performance issues related to MDX queries and calculations, see the MDX optimization section in the [SQL Server Analysis Services Performance Guide](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[The Basic MDX Script (MDX)](../../Topics/TopicNameNotContainA/The-Basic-MDX-Script--MDX-.md)|Details the basic MDX script, including the default MDX script provided in each cube, and how MDX scripts generally function within a cube in [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)].|  
|[Managing Scope and Context (MDX)](../../Topics/TopicNameNotContainA/Managing-Scope-and-Context--MDX-.md)|Describes how to use the [CALCULATE](assetId:///41e196a1-d49e-487b-a42a-73e5d441ed1b) statement, the [SCOPE](assetId:///ceab459d-b601-4468-b3fc-4f5bb4a1805f) statement, and the [This](assetId:///87acddee-ae54-49ee-8923-1b760606e8b7) function to manage context and scope within an MDX script.|  
|[Using Variables and Parameters (MDX)](../../Topics/TopicNameNotContainA/Using-Variables-and-Parameters--MDX-.md)|Describes how to use variables and parameters in an MDX script.|  
|[Error Handling (MDX)](../../Topics/TopicNameNotContainA/Error-Handling--MDX-.md)|Explains error handling within an MDX script.|  
|[Supported MDX (MDX)](../../Topics/TopicNameNotContainA/Supported-MDX--MDX-.md)|Provides a list of supported MDX operators, statements, and functions within an MDX script.|  
  
## See Also  
 [MDX Language Reference (MDX)](assetId:///8ceaedd3-7679-4300-83a5-4809243cdc5d)