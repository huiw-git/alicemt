---
title: Data Mining Stored Procedures (Analysis Services - Data Mining)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a751856d-33bd-4788-9593-317b2826132d
---
# Data Mining Stored Procedures (Analysis Services - Data Mining)
  Beginning in [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] supports stored procedures that can be written in any managed language. The managed languages that are supported include [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] .NET, C\#, and managed C\+\+. In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], you can call the stored procedures directly by using the **CALL** statement, or as part of a Data Mining Extensions \(DMX\) query.  
  
 For more information about calling [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] stored procedures, see [Calling Stored Procedures](../Topic/Calling%20Stored%20Procedures.md).  
  
 For general information about the programmability of [!INCLUDE[ssASCurrent](../../Token\Other/ssASCurrent_md.md)], see [Data Mining Programming](../Topic/Data%20Mining%20Programming.md).  
  
 For additional information about how to program data mining objects, see the article, "[SQL Server Data Mining Programmability](http://go.microsoft.com/fwlink/?LinkId=93735)", in the MSDN library.  
  
> [!NOTE]  
>  When you query mining models, especially when you test new data mining solutions, you might find it convenient to call the system stored procedures that are used internally by the data mining engine. You can view the names of these system stored procedures by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to create a trace on the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] server, and then creating, browsing, and querying the data mining models. However, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] does not guarantee the compatibility of system stored procedures between versions, and you should never use calls to the system stored procedures in a production system. Instead, for compatibility, you should create your own queries by using DMX or XML\/A.  
  
## In This Section  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services - Data Mining&#41;](../Topic/SystemGetCrossValidationResults%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
-   [SystemGetClusterCrossValidationResults &#40;Analysis Services - Data Mining&#41;](../Topic/SystemGetClusterCrossValidationResults%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services - Data Mining&#41;](../Topic/SystemGetAccuracyResults%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
-   [SystemGetClusterAccuracyResults &#40;Analysis Services - Data Mining&#41;](../Topic/SystemGetClusterAccuracyResults%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
## Reference  
 [Script Administrative Tasks in Analysis Services](../../Topics\TopicNameNotContainA/Script-Administrative-Tasks-in-Analysis-Services.md)  
  
## See Also  
 [Cross-Validation &#40;Analysis Services - Data Mining&#41;](../Topic/Cross-Validation%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Cross-Validation Tab &#40;Mining Accuracy Chart View&#41;](../Topic/Cross-Validation%20Tab%20\(Mining%20Accuracy%20Chart%20View\).md)   
 [Calling a Stored Procedure](../Topic/Calling%20a%20Stored%20Procedure.md)  
  
  