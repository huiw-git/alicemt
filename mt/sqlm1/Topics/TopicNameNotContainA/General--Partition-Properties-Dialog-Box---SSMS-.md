---
title: General (Partition Properties Dialog Box) (SSMS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: efb505be-354f-4d23-8f2d-3e76fa50d27b
---
# General (Partition Properties Dialog Box) (SSMS)
  Use the **General** page of the **Partition Properties** dialog box in SQL Server Management Studio to set the general properties of a partition in a measure group for a cube in an [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database.  
  
## Options  
  
|Term|Definition|  
|----------|----------------|  
|**Aggregation Design ID**|Displays the identifier of the aggregation design used by the partition.|  
|**Aggregation Prefix**|Displays the default prefix of aggregation instances that are contained by the partition.|  
|**Create Timestamp**|Displays the date and time the partition was created.|  
|**Current Storage Mode**|Displays the current storage mode of the partition.<br /><br /> Note: This mode may vary depending on the proactive caching settings for the partition. For more information about proactive caching, see [Proactive Caching &#40;Partitions&#41;](../Topic/Proactive%20Caching%20\(Partitions\).md).|  
|**Description**|Type to change the description of the partition.|  
|**Estimated Rows**|Type the estimated number of rows in the underlying data source represented by the partition. This value is used during processing to estimate the time and storage required to process the partition.|  
|**Estimated Size**|Displays the estimated size of the partition.|  
|**ID**|Displays the identifier of the partition.|  
|**Last Processed**|Displays the date and time the partition was last processed.|  
|**Last Schema Update**|Displays the date and time the metadata for the partition was last updated.|  
|**Name**|Displays the name of the partition.|  
|**Processing Mode**|Select the processing mode for the partition. For more information about processing modes for [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects, see [Processing a multidimensional model &#40;Analysis Services&#41;](../Topic/Processing%20a%20multidimensional%20model%20\(Analysis%20Services\).md).|  
|**Remote Data Source ID**|Displays the identifier of the remote data source from which the source data for the partition is retrieved.<br /><br /> Note: This property contains a value only for remote partitions.|  
|**Slice**|Displays the expression that identifies the data slice represented by the partition.|  
|**Source**|Displays the table or query that provides the source data for the partition.|  
|**State**|Displays the current processing state of the partition.|  
|**Storage Location**|Displays the folder in which the data for the partition is stored.<br /><br /> Note: This property contains a value only if a storage location other than the default storage location for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance is specified.|  
|**Type**|Displays the type of the partition.|  
  
## See Also  
 [Partitions &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Partitions%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Remote Partitions](../Topic/Remote%20Partitions.md)   
 [Partition Properties Dialog Box &#40;SSMS&#41;](../Topic/Partition%20Properties%20Dialog%20Box%20\(SSMS\).md)   
 [Selection &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](../Topic/Selection%20\(Partition%20Properties%20Dialog%20Box\)%20\(SSMS\).md)   
 [Proactive Caching &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](../Topic/Proactive%20Caching%20\(Partition%20Properties%20Dialog%20Box\)%20\(SSMS\).md)   
 [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](../Topic/Error%20Configuration%20for%20Cube,%20Partition,%20and%20Dimension%20Processing%20\(SSAS%20-%20Multidimensional\).md)  
  
  