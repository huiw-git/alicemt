---
title: Building Cell Calculations in MDX (MDX)
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
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
---
# Building Cell Calculations in MDX (MDX)
  Multidimensional Expressions (MDX) provides you with a number of tools for generating calculated values, such as calculated members, custom rollups, and custom members. However, using these features to affect a specific set of cells, or a single cell for that matter, would be difficult.  
  
 To generated calculated values for specifically for cells, you need to use the calculated cells feature in MDX. Calculated cells let you define a specific slice of cells, called a *calculation subcube*, and apply a formula to each and every cell within the calculation subcube, subject to an optional condition that can be applied to each cell.  
  
 Calculated cells also offer complex functionality, such as goal-seeking formulas, as used in KPIs, or speculative analysis formulas. This level of functionality comes from the pass order feature in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)] that allows recursive passes to be made with calculated cells, with calculation formulas applied at specific passes in the pass order. For more information on pass order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](../../Topics/TopicNameNotContainA/Understanding-Pass-Order-and-Solve-Order--MDX-.md).  
  
 In terms of creation scope, calculated cells are similar to both named sets and calculated members in that calculated cells can be temporarily created for the lifetime of either a session or a single query, or made globally available as part of a cube:  
  
-   **Query-scoped** To create a calculated cell that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword. You can then use the calculated cell within an MDX SELECT statement. Using this approach, the calculated cell created by using the **WITH** keyword can be changed without disturbing the SELECT statement.  
  
     For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../Topics/TopicNameNotContainA/Creating-Query-Scoped-Cell-Calculations--MDX-.md).  
  
-   **Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use either the CREATE CELL CALCULATION or ALTER CUBE statement.  
  
     For more information about how to use either the CREATE CELL CALCULATION or ALTER CUBE statement to create calculated cells in a session, see [Creating Session-Scoped Calculated Cells](../../Topics/TopicNameNotContainA/Creating-Session-Scoped-Calculated-Cells.md)  
  
## See Also  
 [ALTER CUBE Statement &#40;MDX&#41;](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md)   
 [CREATE CELL CALCULATION Statement &#40;MDX&#41;](../Topic/CREATE%20CELL%20CALCULATION%20Statement%20\(MDX\).md)   
 [Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../Topics/TopicNameNotContainA/Creating-Query-Scoped-Cell-Calculations--MDX-.md)   
 [MDX Query Fundamentals &#40;Analysis Services&#41;](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)  
  
  