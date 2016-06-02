---
title: Delete a Mining Model from a Mining Structure
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
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
---
# Delete a Mining Model from a Mining Structure
  You can delete mining models by using Data Mining Designer, by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], or by using DMX statements.  
  
### Delete a mining model using SQL Server Data Tools  
  
1.  Select the **Mining Models** tab in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
2.  Right\-click the model that you want to delete, and select **Delete**.  
  
     The **Delete Objects** dialog box opens.  
  
3.  Click **OK**.  
  
### Delete a mining model using SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], open the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database that contains the model.  
  
2.  Expand **Mining Structures**, and then expand **Mining Models**.  
  
3.  Right\-click the model you want to delete, and select **Delete**.  
  
     Deleting the model does not delete the training data, only the metadata and any patterns created when you trained the model.  
  
### Delete a mining model using DMX  
  
-   [DROP MINING MODEL &#40;DMX&#41;](../Topic/DROP%20MINING%20MODEL%20\(DMX\).md)  
  
## See Also  
 [Mining Model Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Model-Tasks-and-How-tos.md)  
  
  