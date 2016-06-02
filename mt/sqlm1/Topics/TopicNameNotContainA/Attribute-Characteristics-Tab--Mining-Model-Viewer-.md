---
title: Attribute Characteristics Tab (Mining Model Viewer)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
---
# Attribute Characteristics Tab (Mining Model Viewer)
  Use the **Attribute Characteristics** pane to explore the relationships between outcomes and input attributes in a Naïve Bayes model. You can choose the value of the target attribute, and then see a list of the input attributes that have the strongest effect on the outcomes.  
  
 **For More Information:** [Microsoft Naive Bayes Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Naive-Bayes-Algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Naive-Bayes-Viewer.md)  
  
## Options  
 **Refresh viewer content**  
 Reload the mining model in the viewer.  
  
 **Mining Model**  
 Choose a mining model to view, from the models in the current mining structure. The mining model will automatically open in a custom viewer that is best for the particular type of model you chose.  
  
 **Viewer**  
 Choose a viewer to use to explore the selected mining model. For each model, you have the choice of a custom viewer, or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Mining Content Viewer. Plug\-in viewers also appear in this list if available.  
  
 **Attribute**  
 Choose the predictable attribute that you want to analyze.  
  
 **Value**  
 Choose a state for the predictable attribute that you set in **Attribute**. Because Naïve Bayes models do not support continuous variables, all target attributes have discrete or discretized outcomes. The Missing attribute is always automatically added to the list.  
  
 **Characteristics for \<predictable state\>**  
 The graph contains the following columns, which describe how states of the input attributes are related to the selected predictable attribute state.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable**|Lists the input attributes in the mining model.|  
|**Values**|Lists each state of the input attribute in **Variable**.|  
|**Probability**|The bar represents the probability that the attribute and value in that row are associated with the selected state of the predictable attribute. Hover the mouse over the bar to view the probability as a percentage.|  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
  