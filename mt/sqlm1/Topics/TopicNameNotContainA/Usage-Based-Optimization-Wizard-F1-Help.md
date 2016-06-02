---
title: Usage-Based Optimization Wizard F1 Help
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
---
# Usage-Based Optimization Wizard F1 Help
  The Usage\-Based Optimization Wizard is similar in output to the Aggregation Design Wizard, and is used to design aggregations for a partition. However, the Usage\-Based Optimization Wizard designs aggregations based on the specific usage patterns of queries recorded in the query log of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance. Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] to retrieve pre\-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.  
  
 To open the Usage\-Based Optimization Wizard from within [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the cube designer for an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, and then click the **Aggregations** tab. Click the **Usage Based Optimization** button in the toolbar.  
  
 To open the Usage\-Based Optimization Wizard from within [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database and then open the **Cubes** folder. Select a cube and then open the **Measure Groups** folder and expand the measure group that you want to modify. Right\-click the **Partitions** folder and then select **Usage Based Optimization**.  
  
 To design these aggregations, you can use the Aggregation Design Wizard. This wizard guides you through the following steps:  
  
-   Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.  
  
-   Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.  
  
-   Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.  
  
-   Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.  
  
 [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides the Aggregation Design Wizard to design aggregations based on statistical analysis of the structure of the partition to deliver an aggregation design that can be limited by storage size or estimated performance gain. You can use the Aggregation Design Wizard to improve the overall performance of a partition, but the aggregation design is not targeted to the specific needs of your business users. The Usage\-Based Optimization Wizard can provide an aggregation design targeted to these specific needs, but the wizard can do so only if the query log for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance contains enough information to construct such queries.  
  
 Typically, both wizards are used together to improve performance both upon deployment and over time. The Aggregation Design Wizard should be used first, when the partition \(or the cube or measure group containing the partition\) is initially deployed, to provide an overall performance benefit. After a period of time during which you have recorded the queries of business users for the partition in the query log, you can then use the Usage\-Based Optimization Wizard to further focus the aggregation design to better serve the performance and query requirements of your business users.  
  
> [!NOTE]  
>  For information about configuring the query log, see [Configuring the Analysis Services Query Log](http://www.microsoft.com/technet/prodtechnol/sql/2005/technologies/config_ssas_querylog.mspx).  
  
## In This Section  
  
-   [Select Partitions to Modify &#40;Usage-Based Optimization Wizard&#41;](../Topic/Select%20Partitions%20to%20Modify%20\(Usage-Based%20Optimization%20Wizard\).md)  
  
-   [Specify Query Criteria &#40;Usage-Based Optimization Wizard&#41;](../Topic/Specify%20Query%20Criteria%20\(Usage-Based%20Optimization%20Wizard\).md)  
  
-   [Review the Queries that will be Optimized &#40;Usage-Based Optimization Wizard&#41;](../Topic/Review%20the%20Queries%20that%20will%20be%20Optimized%20\(Usage-Based%20Optimization%20Wizard\).md)  
  
-   [Review Aggregation Usage &#40;Usage-Based Optimiation Wizard&#41;](../Topic/Review%20Aggregation%20Usage%20\(Usage-Based%20Optimiation%20Wizard\).md)  
  
-   [Specify Object Counts &#40;Usage-Based Optimization Wizard&#41;](../Topic/Specify%20Object%20Counts%20\(Usage-Based%20Optimization%20Wizard\).md)  
  
-   [Set Aggregation Options &#40;Usage-Based Optimization Wizard&#41;](../Topic/Set%20Aggregation%20Options%20\(Usage-Based%20Optimization%20Wizard\).md)  
  
-   [Completing the Wizard &#40;Usage-Based Optimization Wizard&#41;](../Topic/Completing%20the%20Wizard%20\(Usage-Based%20Optimization%20Wizard\).md)  
  
## See Also  
 [Aggregations and Aggregation Designs](../Topic/Aggregations%20and%20Aggregation%20Designs.md)   
 [Cubes in Multidimensional Models](../../Topics\TopicNameNotContainA/Cubes-in-Multidimensional-Models.md)   
 [Aggregation Design Wizard F1 Help](../../Topics\TopicNameNotContainA/Aggregation-Design-Wizard-F1-Help.md)   
 [Analysis Services Wizards &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Wizards%20\(Multidimensional%20Data\).md)  
  
  