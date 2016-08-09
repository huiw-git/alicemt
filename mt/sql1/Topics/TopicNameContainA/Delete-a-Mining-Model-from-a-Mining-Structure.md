---
title: "Delete a Mining Model from a Mining Structure"
ms.custom: na
ms.date: 06/29/2016
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
caps.latest.revision: 30
caps.handback.revision: 0
manager: paulettm
---
# Delete a Mining Model from a Mining Structure
You can delete mining models by using Data Mining Designer, by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], or by using DMX statements.  
  
### Delete a mining model using SQL Server Data Tools  
  
1.  Select the **Mining Models** tab in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].  
  
2.  Right-click the model that you want to delete, and select **Delete**.  
  
     The **Delete Objects** dialog box opens.  
  
3.  Click **OK**.  
  
### Delete a mining model using SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], open the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database that contains the model.  
  
2.  Expand **Mining Structures**, and then expand **Mining Models**.  
  
3.  Right-click the model you want to delete, and select **Delete**.  
  
     Deleting the model does not delete the training data, only the metadata and any patterns created when you trained the model.  
  
### Delete a mining model using DMX  
  
-   [DROP MINING MODEL](assetId:///8ff561d0-a526-4712-9fff-11df9f8c45a1)  
  
## See Also  
 [Mining Model Tasks and How-tos](../../Topics/TopicNameNotContainA/Mining-Model-Tasks-and-How-tos.md)