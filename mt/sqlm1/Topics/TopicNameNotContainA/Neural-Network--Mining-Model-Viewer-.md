---
title: Neural Network (Mining Model Viewer)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
---
# Neural Network (Mining Model Viewer)
  Use the **Neural Net** viewer to explore mining models that are based on the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Logistic Regression algorithm.  
  
 **For More Information:** [Microsoft Neural Network Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Neural-Network-Algorithm.md), [Microsoft Logistic Regression Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm.md),[Browse a Model Using the Microsoft Neural Network Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Neural-Network-Viewer.md)  
  
## Options  
 **Refresh viewer content**  
 Reload the mining model in the viewer.  
  
 **Mining Model**  
 Choose a mining model to view, from those in the current mining structure. The mining model will open in its associated viewer.  
  
 **Viewer**  
 Choose a viewer to use to explore the selected mining model. You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**. You can also use plug\-in viewers if available.  
  
 **Input**  
 Use this area to choose input attributes and values, so that you can later explore how these affect the outcome.  
  
|Value|Description|  
|-----------|-----------------|  
|**Attribute**|Choose an input attribute from the list. If you leave the selection as the default, **\<All\>**, the chart shows a list of all input attributes, ranked by their impact on the predictable attribute.|  
|**Value**|Choose a value for the input attribute.|  
  
 **Output**  
 Use these controls to choose a predictable attribute and value to analyze and compare in the bar graph. If you do not change the selections, the bar graph compares the top two outcome states.  
  
|Value|Description|  
|-----------|-----------------|  
|**Output Attribute**|Choose a predictable attribute. If you did not define the column as a predictable one when you created the model, you cannot add it here.|  
|**Value 1**|Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.<br /><br /> You can compare any two discrete or discretized values; however, you cannot compare a value to its complement, as you can in other viewers.|  
|**Value 2**|Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.|  
  
 **Variables**  
 This part of the **Neural Network** tab contains an interactive bar graph, which responds to the selections that you made for input and outcome attributes. Because a neural network calculates the likelihood that a particular value influences a particular outcome, you can choose any combination of inputs, and the bar chart will display how that combination affects the pair of outcomes that you are comparing.  
  
|Value|Description|  
|-----------|-----------------|  
|**Attribute**|Shows the name of the input attribute you selected in **Attribute**.|  
|**Value**|Shows the value for the selected input attribute.|  
|**Favors \<Value 1\>**|Displays a bar that indicates how much this particular attribute\-value combination affects the target outcome chosen in **Value 1**.|  
|**Favors \<Value 2\>**|Displays a bar that indicates how much this particular attribute\-value combination affects the target outcome chosen in **Value 2**.|  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
  