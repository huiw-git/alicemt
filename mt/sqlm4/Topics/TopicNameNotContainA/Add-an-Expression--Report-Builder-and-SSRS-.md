---
title: Add an Expression (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
---
# Add an Expression (Report Builder and SSRS)
  Expressions are used throughout a report for defining report item properties, filters, groups, sort order, connection strings, and parameter values. Expressions begin with an equal sign \(\=\) and are written in [!INCLUDE[msCoName](../../Token/Other/msCoName_md.md)] [!INCLUDE[vbprvb](../../Token/Other/vbprvb_md.md)]. They are evaluated at run time by the report processor, which combines the evaluation result with report layout elements.  
  
 Expressions can be simple or complex. Simple expression refer to a single item in a built\-in collection. Complex expressions can contain constants, operators, global collection items, and function calls. For more information, see [Expressions &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token/Other/ssRBRDDup_md.md)]  
  
### To add an expression to a text box  
  
-   In **Design** view, click the text box on the design surface to which you want to add an expression.  
  
    -   For a simple expression, type the display text for the expression in the text box. For example, for the dataset field Sales, type `[Sales]`.  
  
    -   For a complex expression, right\-click the text box, and select **Expression**. The **Expression** dialog box opens. Type or interactively create your expression after the '\=' in the expression pane, and then click OK.  
  
         The expression appears on the design surface as `<<Expr>>`.  
  
## See Also  
 [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Formatting-Text-and-Placeholders--Report-Builder-and-SSRS-.md)   
 [Text Boxes &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Text-Boxes--Report-Builder-and-SSRS-.md)   
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Expression-Uses-in-Reports--Report-Builder-and-SSRS-.md)   
 [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Filter-Equation-Examples--Report-Builder-and-SSRS-.md)   
 [Group Expression Examples &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Group-Expression-Examples--Report-Builder-and-SSRS-.md)   
 [Expression Dialog Box &#40;Report Builder&#41;](../../Topics/TopicNameNotContainA/Expression-Dialog-Box--Report-Builder-.md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Expression-Examples--Report-Builder-and-SSRS-.md)   
 [Add Code to a Report &#40;SSRS&#41;](../../Topics/TopicNameContainA/Add-Code-to-a-Report--SSRS-.md)  
  
  