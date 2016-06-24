---
title: Filter an Itemset in an Association Rules Model
H1: na
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
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
---
# Filter an Itemset in an Association Rules Model
  In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)], you can filter the itemsets that are displayed in the **Itemsets** tab of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] Association Rules Viewer.  
  
### To filter an itemset  
  
1.  On the **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/includes/ssBIDevStudioFull_md.md)], click the **Itemsets** tab of the **Association Rules Viewer**.  
  
2.  Enter a rule condition in the **Filter itemset** box. For example, a rule condition might be "Touring-1000 = existing"  
  
3.  Click **Enter**.  
  
 The itemsets are now filtered to display only those itemsets that contain the selected items. The box is not case-sensitive. Filters are stored in memory so that you can select an old filter from the list.  
  
## See Also  
 [Mining Model Viewer Tasks and How-tos](../../Topics/TopicNameNotContainA/Mining-Model-Viewer-Tasks-and-How-tos.md)  
  
  