---
title: Sequence Clustering Cluster Diagram Tab (Mining Model Viewer
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b705397-9af4-4678-9eda-149bc5d762fa
---
# Sequence Clustering Cluster Diagram Tab (Mining Model Viewer
  The **Cluster Diagram** tab in the **Microsoft Sequence Clustering Viewer** provides a graphical view of all the clusters that the sequence clustering model contains.  
  
 Use this view of a sequence clustering model to drill through from each cluster to the supporting cases, if drillthrough has been enabled. You can also assign descriptive names to the clusters, and change the shading variable to assess the distribution of values at a glance  
  
 **For More Information:** [Microsoft Sequence Clustering Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Sequence-Cluster-Viewer.md)  
  
## Options  
 **Refresh viewer content**  
 Reload the mining model in the viewer.  
  
 **Mining Model**  
 Choose a mining model to view that is contained in the current mining structure. The mining model will open in its associated viewer.  
  
 **Viewer**  
 Choose a viewer to use in exploring the selected mining model. You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**. You can also use plug\-in viewers if available.  
  
 **Zoom In**  
 Zoom in to the diagram, to get a more detailed view of the clusters.  
  
 **Zoom Out**  
 Zoom out from the diagram, to see all the clusters in the model.  
  
 **Copy Graph View**  
 Copy the visible section of the diagram to the clipboard.  
  
 **Copy Entire Graph**  
 Copy the complete diagram to the clipboard.  
  
 **Scale diagram to fit window**  
 Zoom out from the diagram until the whole diagram fits within the screen.  
  
 **Find Node**  
 Use the **Find Node** dialog box to filter the clusters in the graph and make it easier to find a specific cluster. For more information, see [Find Node Dialog Box &#40;Mining Model Viewer&#41;](../Topic/Find%20Node%20Dialog%20Box%20\(Mining%20Model%20Viewer\).md).  
  
 Note that in this context, you are searching only the name of the cluster, not the attributes within the cluster; therefore, this option is most useful if you have assigned descriptive names to your cluster. You can assign names to clusters in the viewer by right\-clicking each cluster and selecting **Rename**.  
  
 **Improve Layout**  
 Reorder the clusters in the diagram to improve the layout.  
  
 **Density**  
 The appearance of the density bar graph and the values in it are dependent on the attribute that you select in **Shading Variable**.  
  
-   If no attribute state is selected as the shading variable, by default the density shading applied to each cluster represents the support for the cluster, compared to the overall population of cases.  
  
-   When you select an attribute for **Shading Variable**, you must then select a value for **State** as well. When you do so, the density bar graph updates to show the probability of this state. You can pause the mouse over any individual cluster to see the probability of the selected state for the cluster.  
  
 **Shading Variable**  
 Select an attribute from the mining model to use in shading the cluster diagram.  
  
 **State**  
 Select a state that corresponds to the **Shading Variable**. For example, if you want to view the sequences that include a particular product, you would select the \[Product\] column as the attribute for **Shading Variable**, and the specific product name as the **State** value.  
  
 **Links**  
 The lines in the diagram indicate associations between sequence clusters. You can adjust how many links the viewer shows by adjusting the slider to the right of the clusters. Lowering the slider shows only the strongest links.  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
  