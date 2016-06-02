---
title: Cluster Discrimination Tab (Mining Model Viewer)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
---
# Cluster Discrimination Tab (Mining Model Viewer)
  Use the **Cluster Discrimination** tab to compare two clusters that exist in a clustering model. You can see how different combinations of attributes and values are represented within the clusters.  
  
 **For More Information:** [Microsoft Clustering Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Clustering-Algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Cluster-Viewer.md)  
  
## Options  
 **Refresh viewer content**  
 Reload the mining model in the viewer.  
  
 **Mining Model**  
 Choose a mining model from those in the current mining structure. The mining model will open in its associated viewer.  
  
 **Viewer**  
 Choose a viewer to use to explore the selected mining model. You can use the custom viewer for clustering models, or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Mining Content Viewer. You can also use plug\-in viewers if available.  
  
 **Cluster 1**  
 Select a cluster, so that you can compare it to another cluster.  
  
 **Cluster 2**  
 Select a second cluster from the list of clusters in the mining model, to compare to **Cluster 1**. You can also compare a cluster to its complement, meaning all cases in the model except those in the selected cluster.  
  
 **Discrimination scores for \<cluster 1\> and \<cluster 2\>**  
 The columns in the graph provide information about how each attribute\-value pair is related to the two selected clusters.  
  
|||  
|-|-|  
|**Variables**|An attribute in the mining model.|  
|**Values**|A value of the attribute selected in **Variables**.|  
|**Favors \<cluster 1\>**|The bar graph on the left represents the probability that the selected attribute\-value pair is representative of the cluster selected in **Cluster 1**. You can pause the mouse over the bar to see the value, represented as a percentage. Note that even if the value is zero, it doesn’t mean the attribute\-value is necessarily missing from the cluster, just that the distribution strongly favors one cluster over the other.|  
|**Favors \<cluster 2\>**|The bar graph on the right represents the probability that the selected attribute\-value pair is representative of the cluster selected in **Cluster 2**.|  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Model Viewers &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Model%20Viewers%20\(Data%20Mining%20Model%20Designer\).md)   
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
  