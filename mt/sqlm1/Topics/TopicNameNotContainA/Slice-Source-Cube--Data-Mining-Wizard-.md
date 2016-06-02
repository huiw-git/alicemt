---
title: Slice Source Cube (Data Mining Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
---
# Slice Source Cube (Data Mining Wizard)
  You can use the **Slice Source Cube** dialog box to restrict the data used to train the model. Typically a cube contains data related to many different dimensions and attributes, such as all stores, all regions, and all products. It is not practical to train a model on unlimited combinations of attributes, so you use this dialog box to choose a specific set to use in training a model.  
  
 For example, in the AdventureWorks cube, you might slice by a particular product line, region, or year, to get a portion of the data.  
  
> [!NOTE]  
>  Note that dynamic MDX functions \(such as [Generate &#40;MDX&#41;](../Topic/Generate%20\(MDX\).md) or [Except &#40;MDX&#41;](../Topic/Except%20\(MDX\).md)\) are not supported in the Slice property for partitions. You must define the slice by using explicit tuples or member references.  
>   
>  For example, rather than using the range operator \(:\) to define a range, you would need to enumerate each member by the specific years.  
>   
>  If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script. Then, you can use either the ascmd command\-line tool or the [Analysis Services Execute DDL Task](../../Topics\TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md) in Integration Services to run the script and create the specified set of members immediately before you process the partition.  
  
 **For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20\(Analysis%20Services%20-%20Data%20Mining\).md), [Create a Relational Mining Structure](../../Topics\TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Dimension**  
 Select the dimension that you want to slice.  
  
 **Hierarchy**  
 Select the hierarchy that you want to slice. You can choose any level of a hierarchy, but the attributes used in the model will be only at the level that you choose.  
  
 For example, if you choose the Geography hierarchy, and select Country as the level, you cannot build a model that uses City as the attributes. Conversely, if you choose City as the level of the hierarchy on which to slice, you cannot create a mining model based on Country.  
  
 **Operator**  
 Select the operator to use in building a slice expression.  
  
 For example, if you chose Geography as the hierarchy, you could select the operator \= and then type “Europe” as the filter, to get cube data for Europe only.  
  
 **Filter Expression**  
 Type an expression to use as a criterion when filtering the cube on the selected dimension.  
  
 **Parameters**  
 This option is not used for data mining models.  
  
## See Also  
 [Completing the Wizard &#40;Data Mining Wizard&#41;](../Topic/Completing%20the%20Wizard%20\(Data%20Mining%20Wizard\).md)   
 [Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Specify Mining Model Column Usage &#40;Data Mining Wizard&#41;](../Topic/Specify%20Mining%20Model%20Column%20Usage%20\(Data%20Mining%20Wizard\).md)  
  
  