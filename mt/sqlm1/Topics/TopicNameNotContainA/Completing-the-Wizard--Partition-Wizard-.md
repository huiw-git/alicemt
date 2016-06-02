---
title: Completing the Wizard (Partition Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
---
# Completing the Wizard (Partition Wizard)
  Use the **Completing the Wizard** page to name the partition, define the aggregation design for your partition, and optionally deploy and process the partition after completing the Partition Wizard.  
  
## Options  
 **Name**  
 Type the name for the new partition. If you are working with multiple tables, enter the prefix that will be combined with the table name to create each partition name.  
  
 **Aggregation options**  
 Specifies the aggregation option for the partition.  
  
 The following table lists the aggregation options that are available.  
  
|Option|Description|  
|------------|-----------------|  
|**Design aggregations for the partition now**|Designs aggregations for the new partition after the Partition Wizard creates the new partition. Selecting this option starts the Aggregation Design Wizard after you click **Finish** in the Partition Wizard. For more information about the Aggregation Design Wizard, see [Aggregation Design Wizard F1 Help](../../Topics\TopicNameNotContainA/Aggregation-Design-Wizard-F1-Help.md).|  
|**Design the aggregations later**|Creates the partition without designing aggregations at this time.|  
|**Copy the aggregation design from an existing partition**|Copies the aggregation design from an existing partition in the measure group to the new partition. Clicking this option makes the **Copy from** option available. Use the **Copy from** option to select the partition from which to copy the aggregation design.<br /><br /> Note: Partitions that may be merged in the future must have the same table structure and aggregation design. If you might merge the new partition with an existing partition in the measure group, you should copy the aggregation design of the existing partition into the new partition.|  
  
 **Deploy and Process Now**  
 Deploys and processes the partition to the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance specified on the **Processing and Storage Locations** page. The wizard deploys and processes the partition after you click **Finish** on this page.  
  
## See Also  
 [Partitions &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Partitions%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  