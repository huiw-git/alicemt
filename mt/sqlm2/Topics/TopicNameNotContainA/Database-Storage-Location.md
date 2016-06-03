---
title: Database Storage Location
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
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
---
# Database Storage Location
  There are often situations when an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database administrator \(dba\) wants a certain database to reside outside of the server data folder. These situations are often driven by business needs, such as improving performance or expanding storage. For these situations, the **DbStorageLocation** database property enables the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] dba to specify the database location in a local disk or network device.  
  
## DbStorageLocation database property  
 The **DbStorageLocation** database property specifies the folder where [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] creates and manages all the database data and metadata files. All metadata files are stored at the **DbStorageLocation** folder, with the exception of the database metadata file, which is stored in the server data folder. There are two important considerations when setting the value of **DbStorageLocation** database property:  
  
-   The **DbStorageLocation** database property must be set to an existing UNC folder path or an empty string. An empty string is the default for the server data folder. If the folder does not exist, an error will be raised when you execute a **Create**, **Attach**, or **Alter** command.  
  
-   The **DbStorageLocation** database property cannot be set to point to the server data folder or any one of its subfolders. If the location points to the server data folder or any one of its subfolders, an error will be raised when you execute a **Create**, **Attach**, or **Alter** command.  
  
> [!IMPORTANT]  
>  We recommend that set your UNC path to use a Storage Area Network \(SAN\), iSCSI\-based network, or a locally attached disk. Any UNC path to a network share or any high latency remote storage solution leads to an unsupported installation.  
  
### DbStorageLocation compared to StorageLocation  
 **DbStorageLocation** specifies the folder where all the database data and metadata files reside, whereas **StorageLocation** specifies the folder where one or more partitions of a cube reside. **StorageLocation** can be set independently of **DbStorageLocation**. This is an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] dba decision based on the expected results, and many times the usage of one property or the other will overlap.  
  
## DbStorageLocation Usage  
 The **DbStorageLocation** database property is used as part of a **Create** database command in a **Detach**\/**Attach** database commands sequence, in a **Backup**\/**Restore** database commands sequence, or in a **Synchronize** database command. Changing the **DbStorageLocation** database property is considered a structural change in the database object. This means that all metadata must be recreated and the data reprocessed.  
  
> [!IMPORTANT]  
>  You should not change the database storage location by using an **Alter** command. Instead, we recommend that you use a sequence of **Detach**\/**Attach** database commands \(see [Move an Analysis Services Database](../../Topics\TopicNameNotContainA/Move-an-Analysis-Services-Database.md), [Attach and Detach Analysis Services Databases](../../Topics\TopicNameNotContainA/Attach-and-Detach-Analysis-Services-Databases.md)\).  
  
## See Also  
 [DbStorageLocation](assetId:///P:Microsoft.AnalysisServices.Database.DbStorageLocation)   
 [Attach and Detach Analysis Services Databases](../../Topics\TopicNameNotContainA/Attach-and-Detach-Analysis-Services-Databases.md)   
 [Move an Analysis Services Database](../../Topics\TopicNameNotContainA/Move-an-Analysis-Services-Database.md)   
 [DbStorageLocation Element](../Topic/DbStorageLocation%20Element.md)   
 [Create Element &#40;XMLA&#41;](../Topic/Create%20Element%20\(XMLA\).md)   
 [Attach Element](../Topic/Attach%20Element.md)   
 [Synchronize Element &#40;XMLA&#41;](../Topic/Synchronize%20Element%20\(XMLA\).md)  
  
  