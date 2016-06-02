---
title: Exclude a Column from a Mining Model
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
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
---
# Exclude a Column from a Mining Model
  When you create a new mining model, you may not want to use all the columns that exist in the mining structure on which the model is based. For example, you might have added a customer name column for drillthrough, but don’t want to use it for modeling. Or, you might decide to create multiple copies of a column with different discretizations, and use only one of the copies in each model, and ignore the rest. You could also selectively add input columns in several different models to see how the added variable affects the output column.  
  
 You do not need to create a new mining structure for each combination of columns; instead, you can simply flag a column as not being used in a particular model.  
  
### To exclude a column from a mining model  
  
1.  In the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], select the cell that corresponds to the column you want to exclude, under the appropriate mining model.  
  
2.  Select **Ignore** from the drop\-down list box.  
  
## See Also  
 [Mining Model Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Model-Tasks-and-How-tos.md)  
  
  