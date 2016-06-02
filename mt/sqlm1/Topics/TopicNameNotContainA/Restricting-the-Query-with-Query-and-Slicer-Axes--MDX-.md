---
title: Restricting the Query with Query and Slicer Axes (MDX)
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
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
---
# Restricting the Query with Query and Slicer Axes (MDX)
  When formulating a Multidimensional Expressions \(MDX\) SELECT statement, an application typically examines a cube and divides the set of hierarchies into two subsets:  
  
-   **Query axes**—the set of hierarchies from which data is retrieved for multiple members. For more information about query axes, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](../Topic/Specifying%20the%20Contents%20of%20a%20Query%20Axis%20\(MDX\).md).  
  
-   **Slicer axis**—the set of hierarchies from which data is retrieved for a single member. For more information about the slicer axis, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](../Topic/Specifying%20the%20Contents%20of%20a%20Slicer%20Axis%20\(MDX\).md).  
  
 Because query and slicer axes can be constructed from multiple hierarchies of the cube to be queried, these terms are used to differentiate the hierarchies used by the cube that is to be queried from the hierarchies created in the cube returned by an MDX query.  
  
 To see a simple example using query and slicer axes, see [Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](../Topic/Using%20Query%20and%20Slicer%20Axes%20in%20a%20Simple%20Example%20\(MDX\).md).  
  
## See Also  
 [Working with Members, Tuples, and Sets &#40;MDX&#41;](../Topic/Working%20with%20Members,%20Tuples,%20and%20Sets%20\(MDX\).md)   
 [MDX Query Fundamentals &#40;Analysis Services&#41;](../Topic/MDX%20Query%20Fundamentals%20\(Analysis%20Services\).md)  
  
  