---
title: "Error Handling (MDX)"
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
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 26
caps.handback.revision: 0
manager: mblythe
---
# Error Handling (MDX)
  Each cube can control how errors within a Multidimensional Expressions (MDX) script are handled. Error handling is done through the **ScriptErrorHandlingMode** enumerator. The possible values for this enumerator are:  
  
 **IgnoreNone**  
 Causes the server to raise an error when [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] finds any error in the MDX script.  
  
 **IgnoreAll**  
 Causes the server to ignore all commands in the MDX script that contain an error, including syntax errors, name resolution errors, and more.  
  
## See Also  
 [ScriptErrorHandlingMode](assetId:///P:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode)  
  
  