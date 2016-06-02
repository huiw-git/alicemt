---
title: Proactive Caching (Partition Properties Dialog Box) (SSMS)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecba72a3-703f-4ede-9d85-9a3318a749e5
---
# Proactive Caching (Partition Properties Dialog Box) (SSMS)
  Use the **Proactive Caching** page of the **Partition Properties** dialog box in SQL Server Management Studio to set the storage and proactive caching properties of a partition in a measure group for a cube in an [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database.  
  
## Options  
 **Standard setting**  
 Select to enable **Standard setting slider** and use predefined settings for storage mode and proactive caching features.  
  
 **Standard setting slider**  
 Set to one of the predefined settings listed in the following table.  
  
|Setting|Description|  
|-------------|-----------------|  
|**Real\-time ROLAP**|Select to use the following storage and proactive caching settings:<br /><br /> ROLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 0 seconds.<br /><br /> Brings object online immediately.|  
|**Real\-time HOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> HOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 0 seconds.<br /><br /> Updates cache when data changes, with a silence interval of 0 seconds and no silence override interval.<br /><br /> Brings object online immediately.|  
|**Low\-latency MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 30 minutes.<br /><br /> Updates cache when data changes, with a silence interval of 10 seconds and a silence override interval of 10 minutes.<br /><br /> Brings object online immediately.|  
|**Medium\-latency MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Drops outdated cache, with a latency period of 4 hours.<br /><br /> Updates cache when data changes, with a silence interval of 10 seconds and a silence override interval of 10 minutes.<br /><br /> Brings object online immediately.|  
|**Automatic MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.<br /><br /> Enables proactive caching.<br /><br /> Updates cache when data changes, with a silence interval of 0 seconds and no silence override interval.|  
|**Scheduled MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode<br /><br /> Enable proactive caching<br /><br /> Updates cache periodically, with a rebuild interval of 1 day|  
|**MOLAP**|Select to use the following storage and proactive caching settings:<br /><br /> MOLAP storage mode.|  
  
 **Custom setting**  
 Select to explicitly set storage mode, proactive caching, and notification options.  
  
 **Options**  
 Click to display the **Storage Options** dialog box to explicitly set storage mode, proactive caching, and notification options. For more information about the **Storage Options** dialog box, see [Storage Options Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Storage%20Options%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
## See Also  
 [Proactive Caching &#40;Partitions&#41;](../Topic/Proactive%20Caching%20\(Partitions\).md)   
 [Partition Properties Dialog Box &#40;SSMS&#41;](../Topic/Partition%20Properties%20Dialog%20Box%20\(SSMS\).md)   
 [Selection &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](../Topic/Selection%20\(Partition%20Properties%20Dialog%20Box\)%20\(SSMS\).md)   
 [General &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](../Topic/General%20\(Partition%20Properties%20Dialog%20Box\)%20\(SSMS\).md)   
 [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](../Topic/Error%20Configuration%20for%20Cube,%20Partition,%20and%20Dimension%20Processing%20\(SSAS%20-%20Multidimensional\).md)  
  
  