---
title: "General (Partition Properties Dialog Box) (SSMS)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: efb505be-354f-4d23-8f2d-3e76fa50d27b
caps.latest.revision: 13
caps.handback.revision: 0
manager: mblythe
---
# General (Partition Properties Dialog Box) (SSMS)
Use the **General** page of the **Partition Properties** dialog box in SQL Server Management Studio to set the general properties of a partition in a measure group for a cube in an [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database.  
  
## Options  
  
|Term|Definition|  
|----------|----------------|  
|**Aggregation Design ID**|Displays the identifier of the aggregation design used by the partition.|  
|**Aggregation Prefix**|Displays the default prefix of aggregation instances that are contained by the partition.|  
|**Create Timestamp**|Displays the date and time the partition was created.|  
|**Current Storage Mode**|Displays the current storage mode of the partition.<br /><br /> Note: This mode may vary depending on the proactive caching settings for the partition. For more information about proactive caching, see [Error Configuration (Partition Properties Dialog Box) (Analysis Services - Multidimensional Data)](assetId:///422660b2-4d80-4165-b1c9-3963bcde556b).|  
|**Description**|Type to change the description of the partition.|  
|**Estimated Rows**|Type the estimated number of rows in the underlying data source represented by the partition. This value is used during processing to estimate the time and storage required to process the partition.|  
|**Estimated Size**|Displays the estimated size of the partition.|  
|**ID**|Displays the identifier of the partition.|  
|**Last Processed**|Displays the date and time the partition was last processed.|  
|**Last Schema Update**|Displays the date and time the metadata for the partition was last updated.|  
|**Name**|Displays the name of the partition.|  
|**Processing Mode**|Select the processing mode for the partition. For more information about processing modes for [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] objects, see [Processing a multidimensional model (Analysis Services)](../../Topics/TopicNameContainA/Processing-a-multidimensional-model--Analysis-Services-.md).|  
|**Remote Data Source ID**|Displays the identifier of the remote data source from which the source data for the partition is retrieved.<br /><br /> Note: This property contains a value only for remote partitions.|  
|**Slice**|Displays the expression that identifies the data slice represented by the partition.|  
|**Source**|Displays the table or query that provides the source data for the partition.|  
|**State**|Displays the current processing state of the partition.|  
|**Storage Location**|Displays the folder in which the data for the partition is stored.<br /><br /> Note: This property contains a value only if a storage location other than the default storage location for the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance is specified.|  
|**Type**|Displays the type of the partition.|  
  
## See Also  
 [Partitions (SSAS)](assetId:///cd10ad00-468c-4d49-9f8d-873494d04b4f)   
 [Remote Partitions (SSAS)](assetId:///63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb)   
 [Partition Properties Dialog Box (SSMS)](../../Topics/TopicNameNotContainA/Partition-Properties-Dialog-Box--SSMS-.md)   
 [Selection (Partition Properties Dialog Box) (SSMS)](../../Topics/TopicNameNotContainA/Selection--Partition-Properties-Dialog-Box---SSMS-.md)   
 [Proactive Caching (Partition Properties Dialog Box) (SSMS)](../../Topics/TopicNameNotContainA/Proactive-Caching--Partition-Properties-Dialog-Box---SSMS-.md)   
 [Error Configuration for Cube, Partition, and Dimension Processing (SSAS - Multidimensional)](../../Topics/TopicNameNotContainA/Error-Configuration-for-Cube--Partition--and-Dimension-Processing--SSAS---Multidimensional-.md)