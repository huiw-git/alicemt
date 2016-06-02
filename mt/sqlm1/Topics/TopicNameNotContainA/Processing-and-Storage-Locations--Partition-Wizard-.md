---
title: Processing and Storage Locations (Partition Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
---
# Processing and Storage Locations (Partition Wizard)
  Use the **Processing and Storage Locations** page to specify the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance of the cube that owns the partition, as well as the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance that stores the data for the partition. You can define a partition as a remote partition by specifying either a remote [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance or a storage location other than the default storage location. For more information about remote partitions, see [Remote Partitions](../Topic/Remote%20Partitions.md).  
  
## Processing location Options  
 **Current server instance**  
 Makes the current [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance responsible for processing the partition.  
  
 **Remote Analysis Services data source**  
 Makes a remote [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance responsible for processing this partition.  
  
 From the dropdown list, select the data source representing the remote [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance that will be responsible for processing the partition.  
  
> [!NOTE]  
>  An error occurs if you select a data source in which the **Initial Catalog** connection string property is not set to a valid [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, or if the database specified in the **Initial Catalog** connection string property does not support remote partitions \(in other words, the **MasterDatasourceID** property of the specified database is not set to a valid value\).  
  
 **New**  
 Creates a new data source representing the remote [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance responsible for processing the partition.  
  
## Storage location Options  
 **Default server location**  
 Makes the data folder of the current [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance the storage location of the aggregation and indexing data for the partition.  
  
 **Specified folder**  
 Specifies the storage location of the aggregation and indexing data for the partition.  
  
 **...**  
 Displays the **Browse for Remote Folder** dialog box in which you can select a folder for **Specified folder**.  
  
## See Also  
 [Partition Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Partition%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Partitions &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Partitions%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Browse%20for%20Remote%20Folder%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  