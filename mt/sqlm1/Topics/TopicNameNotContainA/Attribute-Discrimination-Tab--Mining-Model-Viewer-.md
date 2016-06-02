---
title: Attribute Discrimination Tab (Mining Model Viewer)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
---
# Attribute Discrimination Tab (Mining Model Viewer)
  Use the **Attribute Discrimination** tab to compare the states of the input attributes and see how they are related to the outcome attribute. The attribute values that make the most difference between the two selected predictable attribute states are listed first.  
  
 **For More Information:** [Microsoft Naive Bayes Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Naive-Bayes-Algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Naive-Bayes-Viewer.md)  
  
## Options  
 **Refresh viewer content**  
 Reload the mining model in the viewer.  
  
 **Mining Model**  
 Choose a mining model from those in the current mining structure. The mining model automatically opens in the correct custom viewer.  
  
 **Viewer**  
 Choose a viewer to use to explore the selected mining model. For each model, you can choose either the custom viewer, or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Mining Content Viewer. You can also use plug\-in viewers if available.  
  
 **Attribute**  
 Choose a predictable attribute.  
  
 **Value 1**  
 Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.  
  
 **Value 2**  
 Select a state of the predictable attribute to compare to the state that is contained in **Value 1**. You can also select **All Other States** to compare the value in **Value 1** with its complement—that is, all other values except Value 1.  
  
 **Discrimination scores for \<Value 1\> and \<Value 2\>**  
 The graph contains the following columns, which describe how the target attribute is related to specific states of the input attribute.  
  
|Value|Description|  
|-----------|-----------------|  
|**Attributes**|An input attribute in the mining model.|  
|**Values**|A state of the attribute that is listed in **Attributes**.|  
|**Favors \<Value 1\>**|The bar indicates whether the current attribute and value favor the target outcome selected in **Value 1**.|  
|**Favors \<Value 2\>**|The bar indicates whether the current attribute and value favor the target outcome selected in **Value 2**.|  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
  