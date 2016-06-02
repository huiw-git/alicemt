---
title: Feature Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
---
# Feature Properties
  Feature properties pertain to product features, most of them advanced, including properties that control links between server instances.  
  
 [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] supports the server properties listed in the following table. For more information about additional server properties and how to set them, see [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md).  
  
 **Applies to:** Multidimensional server mode only  
  
## Properties  
  
|Property|Default|Description|  
|--------------|-------------|-----------------|  
|**ManagedCodeEnabled**|1|A Boolean property that indicates whether CLR storage procedures are enabled.|  
|**LinkInsideInstanceEnabled**|1|A Boolean property that indicates whether a linked object can be created inside the same server instance.|  
|**LinkToOtherInstanceEnabled**|0|A Boolean property that indicates whether objects on remote servers can be linked to.|  
|**LinkFromOtherInstanceEnabled**|0|A Boolean property that indicates whether objects can be linked to from other server instances.|  
|**ConnStringEncryptionEnabled**|1|A Boolean property that indicates whether the connection string is encrypted in the server configuration file.|  
|**UseCachedPageAllocators**|0|A Boolean property that indicates whether cached page allocators are enabled.|  
|**ComUdfEnabled**|0|A Boolean property that indicates whether user\-defined functions defined as COM objects are enabled.|  
|**SQMSupportEnabled**|1|A Boolean property that indicates whether error and feature usage reports are sent to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] automatically.|  
|**ResourceMonitoringEnabled**|1|A Boolean property that indicates whether internal resource monitoring counters are enabled. This property is on by default. When enabled, this property allows counters to collect usage data about CPU, memory, and I\/O activity.<br /><br /> Internal resource monitoring counters are used by Dynamic Management Views \(DMV\) that report on resource utilization. If you disable this property, the DMV queries will still run, but the result set will be invalid. DMVs that depend on this property include the following:<br /><br /> **DISCOVER\_OBJECT\_ACTIVITY**<br /><br /> **DISCOVER\_COMMAND\_OBJECTS**<br /><br /> **DISCOVER\_SESSIONS** \(for SESSION\_READS, SESSION\_WRITES, SESSION\_CPU\_TIME\_MS\)<br /><br /> <br /><br /> Note: On a multi\-core system that uses NUMA architecture, disabling this property can improve query performance, particularly for high multi\-user workloads. You will need to run comparison tests to determine whether query performance is improved as the result of changing this property. For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](http://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## See Also  
 [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md)   
 [Determine the Server Mode of an Analysis Services Instance](../../Topics\TopicNameNotContainA/Determine-the-Server-Mode-of-an-Analysis-Services-Instance.md)   
 [Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services](../Topic/Use%20Dynamic%20Management%20Views%20\(DMVs\)%20to%20Monitor%20Analysis%20Services.md)  
  
  