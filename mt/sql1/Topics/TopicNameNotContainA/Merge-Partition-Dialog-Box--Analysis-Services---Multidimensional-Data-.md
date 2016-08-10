---
title: "Merge Partition Dialog Box (Analysis Services - Multidimensional Data)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
caps.latest.revision: 11
caps.handback.revision: 0
manager: mblythe
---
# Merge Partition Dialog Box (Analysis Services - Multidimensional Data)
Use the **Merge Partition** dialog box in **SQL Server Management Studio** to merge partitions for a measure group in a cube. You can display the **Merge Partition** dialog box by right-clicking the Partitions folder or a partition in **Object Explorer** and selecting **Merge Partitions** from the context menu.  
  
## Options  
 **Server**  
 Select the name of the Analysis Services instance that contains the target partition.  
  
 **Name**  
 Select the name of an existing partition to use as the target partition.  
  
 **Folder**  
 Displays the name of the folder that contains the target partition, if the partition selected in Name does not use the default folder for the Analysis Services instance.  
  
 **Source Partitions**  
 Displays a grind containing the source partitions that can be merged into the target partition.  
  
> [!NOTE]  
>  Only partitions in the same measure group that share the same aggregation design can be merged.  
  
 The grid contains the following columns:  
  
|Column|Description|  
|------------|-----------------|  
|**Merge**|Select to merge the source partition into the target partition.|  
|**Partition Name**|Displays the name of the source partition.|  
|**Last Processed**|Displays the date and time at which the source partition was last processed.|  
  
## See Also  
 [Merging Partitions](assetId:///cd10ad00-468c-4d49-9f8d-873494d04b4f)   
 [Merge Partitions in Analysis Services (SSAS - Multidimensional)](../../Topics/TopicNameNotContainA/Merge-Partitions-in-Analysis-Services--SSAS---Multidimensional-.md)