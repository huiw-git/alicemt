---
title: Drill Through Dialog Box (Mining Model Viewer)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
---
# Drill Through Dialog Box (Mining Model Viewer)
  When you view a mining model by using the **Mining Model Viewer** tab of Data Mining Designer, you can drill through into details about the case data, provided the model has drillthrough enabled. Moreover, if the underlying mining structure has drillthrough enabled, you can also see columns in the mining structure, even if those columns were not included in the mining model. In the column list, the structure columns are prefixed by the "Structure." label.  
  
> [!NOTE]  
>  You cannot enable drillthrough on an existing mining structure. Instead, you must re\-create the mining structure and enable drillthrough during the creation process.  
  
 For information about how to access case data from each of the mining model viewers that support drillthrough, **see** [Drill Through to Case Data from a Mining Model](../../Topics\TopicNameContainA/Drill-Through-to-Case-Data-from-a-Mining-Model.md).  
  
## Options  
 **Cases Classified To**  
 Displays the definition of the rule, itemset, and cluster that are contained in the selected node.  
  
 **Column list**  
 Displays the columns in the model, followed by the structure columns.  
  
 **Note** Structure columns are displayed only if drillthrough is enabled on the mining structure, and if you selected the option, **Model and Structure Columns**. Moreover, you must have drillthrough permissions on both the mining model and the mining structure to view the columns.  
  
 Structure columns that are not included in the model appear as **Structure.\<column name\>**.  
  
> [!NOTE]  
>  You can right\-click anywhere in the column grid and select **Copy All** to copy the drillthrough data, in tab\-delimited format, to the Clipboard. The copied data includes only the case data, not the node definition.  
  
 **Play**  
 Click the green arrow button to refresh the data.  
  
## See Also  
 [Drillthrough Queries &#40;Data Mining&#41;](../Topic/Drillthrough%20Queries%20\(Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Mining Model Viewer Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Model-Viewer-Tasks-and-How-tos.md)  
  
  