---
title: Process Tabular Model Partitions (SSAS Tabular)
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
ms.assetid: 6c498d2b-22d6-4661-bc21-2ee708336c8b
---
# Process Tabular Model Partitions (SSAS Tabular)
  Partitions divide a table into logical parts. Each partition can then be processed \(Refreshed\) independent of other partitions. The tasks in this topic describe how to process partitions in a model database by using the **Process Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
###  <a name="bkmk_create_new"></a> To process a partition  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], right\-click on the table that has the partitions you want to process, and then click **Partitions**.  
  
2.  In the **Partitions** dialog box, in **Partitions**, click on the Process button.  
  
3.  In the **Process Parition\(s\)** dialog box, in the **Mode** listbox, select one of the following process modes:  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Process Default**|Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state. Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.|  
    |**Process Full**|Processes a partition object and all the objects that it contains. When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] drops all data in the object, and then processes the object. This kind of processing is required when a structural change has been made to an object.|  
    |**Process Data**|Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.|  
    |**Process Clear**|Removes all data from a partition.|  
    |**Process Add**|Incrementally update partition with new data.|  
  
4.  In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.  
  
## See Also  
 [Tabular Model Partitions &#40;SSAS Tabular&#41;](../Topic/Tabular%20Model%20Partitions%20\(SSAS%20Tabular\).md)   
 [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](../Topic/Create%20and%20Manage%20Tabular%20Model%20Partitions%20\(SSAS%20Tabular\).md)  
  
  