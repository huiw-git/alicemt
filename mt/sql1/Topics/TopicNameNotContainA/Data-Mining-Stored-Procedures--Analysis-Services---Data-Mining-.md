---
title: "Data Mining Stored Procedures (Analysis Services - Data Mining)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a751856d-33bd-4788-9593-317b2826132d
caps.latest.revision: 27
caps.handback.revision: 0
manager: mblythe
---
# Data Mining Stored Procedures (Analysis Services - Data Mining)
Beginning in [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] supports stored procedures that can be written in any managed language. The managed languages that are supported include [!INCLUDE[vbprvb](../../Topics/TopicNameContainA/tokens/vbprvb_md.md)] .NET, C#, and managed C++. In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], you can call the stored procedures directly by using the **CALL** statement, or as part of a Data Mining Extensions (DMX) query.  
  
 For more information about calling [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] stored procedures, see [Calling Stored Procedures](assetId:///96a9660d-875b-4ee4-b339-90020b1d9895).  
  
 For general information about the programmability of [!INCLUDE[ssASCurrent](../../Topics/TopicNameContainA/tokens/ssASCurrent_md.md)], see [Developer's Guide (Analysis Services - Data Mining)](assetId:///9fd77b16-0b89-44ce-bcf1-7c04b62499da).  
  
 For additional information about how to program data mining objects, see the article, "[SQL Server Data Mining Programmability](http://go.microsoft.com/fwlink/?LinkId=93735)", in the MSDN library.  
  
> [!NOTE]  
>  When you query mining models, especially when you test new data mining solutions, you might find it convenient to call the system stored procedures that are used internally by the data mining engine. You can view the names of these system stored procedures by using [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] to create a trace on the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] server, and then creating, browsing, and querying the data mining models. However, [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] does not guarantee the compatibility of system stored procedures between versions, and you should never use calls to the system stored procedures in a production system. Instead, for compatibility, you should create your own queries by using DMX or XML/A.  
  
## In This Section  
  
-   [SystemGetCrossValidationResults (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/SystemGetCrossValidationResults--Analysis-Services---Data-Mining-.md)  
  
-   [SystemGetClusterCrossValidationResults (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/SystemGetClusterCrossValidationResults--Analysis-Services---Data-Mining-.md)  
  
-   [SystemGetAccuracyResults (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/SystemGetAccuracyResults--Analysis-Services---Data-Mining-.md)  
  
-   [SystemGetClusterAccuracyResults (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/SystemGetClusterAccuracyResults--Analysis-Services---Data-Mining-.md)  
  
## Reference  
 [Script Administrative Tasks in Analysis Services](../../Topics/TopicNameNotContainA/Script-Administrative-Tasks-in-Analysis-Services.md)  
  
## See Also  
 [Cross-Validation (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Cross-Validation--Analysis-Services---Data-Mining-.md)   
 [Cross-Validation Tab (Mining Accuracy Chart View)](../../Topics/TopicNameNotContainA/Cross-Validation-Tab--Mining-Accuracy-Chart-View-.md)   
 [Calling a Stored Procedure](assetId:///d13737f4-f641-45bf-b56c-523e2ffc080f)