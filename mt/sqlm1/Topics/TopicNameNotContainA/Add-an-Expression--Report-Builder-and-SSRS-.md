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
  Expressions are used throughout a report for defining report item properties, filters, groups, sort order, connection strings, and parameter values. Expressions begin with an equal sign \(\=\) and are written in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)]. They are evaluated at run time by the report processor, which combines the evaluation result with report layout elements.  
  
 Expressions can be simple or complex. Simple expression refer to a single item in a built\-in collection. Complex expressions can contain constants, operators, global collection items, and function calls. For more information, see [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To add an expression to a text box  
  
-   In **Design** view, click the text box on the design surface to which you want to add an expression.  
  
    -   For a simple expression, type the display text for the expression in the text box. For example, for the dataset field Sales, type `[Sales]`.  
  
    -   For a complex expression, right\-click the text box, and select **Expression**. The **Expression** dialog box opens. Type or interactively create your expression after the '\=' in the expression pane, and then click OK.  
  
         The expression appears on the design surface as `<<Expr>>`.  
  
## See Also  
 [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Text%20and%20Placeholders%20\(Report%20Builder%20and%20SSRS\).md)   
 [Text Boxes &#40;Report Builder and SSRS&#41;](../Topic/Text%20Boxes%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../Topic/Filter%20Equation%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Group Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Group%20Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Dialog Box &#40;Report Builder&#41;](../Topic/Expression%20Dialog%20Box%20\(Report%20Builder\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add Code to a Report &#40;SSRS&#41;](../Topic/Add%20Code%20to%20a%20Report%20\(SSRS\).md)  
  
  