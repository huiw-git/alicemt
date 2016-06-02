---
title: Sequence Clustering Cluster Characteristics Tab (Mining Model Viewer)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
---
# Sequence Clustering Cluster Characteristics Tab (Mining Model Viewer)
  The **Cluster Characteristics** tab in the **Microsoft Sequence Clustering Viewer** provides a detailed list of the characteristics that define a sequence cluster. Those characteristics can include simple attribute\-value pairs as well as transitions between states.  
  
 Use this view of a sequence clustering model to drill down into the cluster contents, and see the sequences that are representative of a cluster.  
  
 **For More Information:** [Microsoft Sequence Clustering Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Sequence-Cluster-Viewer.md)  
  
## Options  
 **Refresh viewer content**  
 Reload the mining model in the viewer.  
  
 **Mining Model**  
 Choose a mining model to view that is contained in the current mining structure. The mining model will open in its associated viewer.  
  
 **Viewer**  
 Choose a viewer to use in exploring the selected mining model. You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**. You can also use plug\-in viewers if available.  
  
 **Cluster**  
 Choose the cluster you want to view.  
  
 **Characteristics for \<Cluster\>**  
 This table provides a list of the sequences that were assigned to the current cluster, ordered by probability. Remember that a sequence is basically one attribute\-value pair, followed by one or more additional attribute\-value pairs. The combination of sequences and their probabilities are the defining characteristics of each cluster.  
  
 For example, in a sequence clustering model based on market basket analysis, one cluster might have as its top characteristic a customer choosing the sale item and then ending the transaction without purchasing anything more. In a sequence clustering model that seeks to analyze server failures, the primary characteristics of a cluster might be a series of high frequency error events.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable**|This column indicates whether the characteristic is a value, or a transition if:<br /><br /> The characteristic is a value, the **Variable** column contains the attribute name.<br /><br /> The characteristic represents a state transition, the **Variable** column contains the text “Transitions”.|  
|**Values**|The value of this column depends on whether the characteristic is a simple attribute\-value pair, or a state transition representing a common sequence of items or events if:<br /><br /> The characteristic is a value, the **Value** column contains the state.<br /><br /> The characteristic represents a state transition, the **Value** column contains the description of the state transition.|  
|**Probability**|This column displays a bar that indicates the relative probability that this characteristic \(either a simple attribute\-value pair, or some combination of states\) are members of the current cluster.<br /><br /> You can hover the mouse over the par to display the frequency value of the characteristic.|  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
  