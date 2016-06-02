---
title: Sequence Clustering Cluster Transition Tab (Mining Model Viewer)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 40aef457-d69f-4905-a2d3-924c37bd3d97
---
# Sequence Clustering Cluster Transition Tab (Mining Model Viewer)
  The **State Transitions** tab in the **Microsoft Sequence Clustering Viewer** provides a closer look at the transitions between attribute\-value pairs, or states, in the selected cluster.  
  
 Use this view of a sequence clustering model to view patterns. In the diagram, a link represents the probability of a transition, and a node represents a sequence state.  
  
 **For More Information:** [Microsoft Sequence Clustering Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Sequence-Cluster-Viewer.md)  
  
## Options  
 **Refresh viewer content**  
 Reload the mining model in the viewer.  
  
 **Mining Model**  
 Choose a mining model to view that is contained in the current mining structure. The mining model will open in its associated viewer.  
  
 **Viewer**  
 Choose a viewer to use in exploring the selected mining model. You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**. You can also use plug\-in viewers if available.  
  
 **Zoom In**  
 Zoom in to the diagram, to see the states better.  
  
 **Zoom Out**  
 Zoom out from the diagram, to get an overall view of the states in the cluster.  
  
 **Copy Graph View**  
 Copy the visible section of the diagram to the clipboard.  
  
 **Copy Entire Graph**  
 Copy the complete diagram to the clipboard.  
  
 **Cluster**  
 Choose a cluster to display in the viewer. By default, **Population \(All\)** is selected, which means that states and transitions from the entire model are included in the graph. When you choose a particular cluster, only the states and transitions that are in that cluster are displayed.  
  
 **Tip:** You can rename clusters by using the **Cluster Diagram** tab. Just select a cluster, right\-click, and select **Rename**. Renaming clusters with a more descriptive label makes it easier to compare clusters in the **State Transitions** tab.  
  
 **Show Edge Labels**  
 Select this option to display numbers on each edge in the graph that denote the probability of the transition.  
  
 **Links**  
 Use the slider to control the number of states and transitions that are displayed in the chart. Lowering the slider shows only the states and transitions with the highest probability.  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
  