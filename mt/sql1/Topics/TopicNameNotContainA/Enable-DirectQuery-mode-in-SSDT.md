---
title: "Enable DirectQuery mode in SSDT"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 17
caps.handback.revision: 0
manager: mblythe
---
# Enable DirectQuery mode in SSDT
This topic explains how to create a Tabular model in [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)] that runs in DirectQuery mode.  If the model already exists and you want to switch from in-memory to DirectQuery, see [Enable DirectQuery mode in SSMS](../../Topics/TopicNameNotContainA/Enable-DirectQuery-mode-in-SSMS.md).  
  
 To create a model in DirectQuery mode, enable DirectQuery on the solution. When you do so, the designer will also do the following:  
  
-   Disable design features that are incompatible with DirectQuery mode.  
  
-   Validate the existing model, to the extent it contains features, and issue warnings if features are incompatible in the new mode.  
  
-   Empty the cache, assuming the model contains objects and data.  
  
### Enable DirectQuery in a Tabular model  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the solution file.  
  
2.  In Object Explorer, double-click the **Model.bim** file.  
  
3.  In the **Properties** pane, change the property, **DirectQueryMode**, to **On**.  
  
4.  If the model contains a data source and existing data, you'll be prompted to enter database credentials used to connect to the relational database. Any data already existing within the model will be flushed from cache.  
  
5.  For a model that is partially or fully complete, you might get errors about incompatible features. In Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being switched to DirectQuery mode.  
  
6.  Import data to get metadata for the model. You won't get rows, but you will get tables,  columns, and relationships to use as the basis for your model.  
  
    > [!TIP]  
    >  Even in DirectQuery mode on an empty model, you can always view a small built-in rowset for each table. In [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)], click **Table** > **Table Properties** to view the 50-row dataset.  
  
7.  Optionally, add sample or test data so that you can verify model behavior as you build it. Any sample data that you add is used in **Analyze for Excel** or in other client tools that can connect to the workspace database. See [Add  sample data to a DirectQuery model in Design Mode](../../Topics/TopicNameContainA/Add--sample-data-to-a-DirectQuery-model-in-Design-Mode.md) for details.  
  
## See Also  
 [DirectQuery Mode (SSAS Tabular)](../../Topics/TopicNameNotContainA/DirectQuery-Mode--SSAS-Tabular-.md)   
 [Data Sources Supported (SSAS Tabular)](../../Topics/TopicNameNotContainA/Data-Sources-Supported--SSAS-Tabular-.md)   
 [Analyze in Excel (SSAS Tabular)](../../Topics/TopicNameNotContainA/Analyze-in-Excel--SSAS-Tabular-.md)