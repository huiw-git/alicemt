---
title: "Proactive Caching (Partition Properties Dialog Box) (SSMS)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecba72a3-703f-4ede-9d85-9a3318a749e5
caps.latest.revision: 13
caps.handback.revision: 0
manager: mblythe
---
# Proactive Caching (Partition Properties Dialog Box) (SSMS)
Use the **Proactive Caching** page of the **Partition Properties** dialog box in SQL Server Management Studio to set the storage and proactive caching properties of a partition in a measure group for a cube in an [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database.  
  
## Options  
 **Standard setting**  
 Select to enable **Standard setting slider** and use predefined settings for storage mode and proactive caching features.  
  
 **Standard setting slider**  
 Set to one of the predefined settings listed in the following table.  
  
|Setting|Description|  
|-------------|-----------------|  
|**Real-time ROLAP**|Select to use the following storage and proactive caching settings:<br /><br /> ROLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 0 seconds.<br /><br /> Brings object online immediately.|  
|**Real-time HOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> HOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 0 seconds.<br /><br /> Updates cache when data changes, with a silence interval of 0 seconds and no silence override interval.<br /><br /> Brings object online immediately.|  
|**Low-latency MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 30 minutes.<br /><br /> Updates cache when data changes, with a silence interval of 10 seconds and a silence override interval of 10 minutes.<br /><br /> Brings object online immediately.|  
|**Medium-latency MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 4 hours.<br /><br /> Updates cache when data changes, with a silence interval of 10 seconds and a silence override interval of 10 minutes.<br /><br /> Brings object online immediately.|  
|**Automatic MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Updates cache when data changes, with a silence interval of 0 seconds and no silence override interval.|  
|**Scheduled MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode<br /><br /> Enable proactive caching<br /><br /> Updates cache periodically, with a rebuild interval of 1 day|  
|**MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.|  
  
 **Custom setting**  
 Select to explicitly set storage mode, proactive caching, and notification options.  
  
 **Options**  
 Click to display the **Storage Options** dialog box to explicitly set storage mode, proactive caching, and notification options. For more information about the **Storage Options** dialog box, see [Storage Options Dialog Box (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Storage-Options-Dialog-Box--Analysis-Services---Multidimensional-Data-.md).  
  
## See Also  
 [Proactive Caching (SSAS)](assetId:///422660b2-4d80-4165-b1c9-3963bcde556b)   
 [Partition Properties Dialog Box (SSMS)](../../Topics/TopicNameNotContainA/Partition-Properties-Dialog-Box--SSMS-.md)   
 [Selection (Partition Properties Dialog Box) (SSMS)](../../Topics/TopicNameNotContainA/Selection--Partition-Properties-Dialog-Box---SSMS-.md)   
 [General (Partition Properties Dialog Box) (SSMS)](../../Topics/TopicNameNotContainA/General--Partition-Properties-Dialog-Box---SSMS-.md)   
 [Error Configuration for Cube, Partition, and Dimension Processing (SSAS - Multidimensional)](../../Topics/TopicNameNotContainA/Error-Configuration-for-Cube--Partition--and-Dimension-Processing--SSAS---Multidimensional-.md)