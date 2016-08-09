---
title: "Deprecated Analysis Services Features in SQL Server 2016"
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
caps.latest.revision: 53
caps.handback.revision: 0
manager: mblythe
---
# Deprecated Analysis Services Features in SQL Server 2016
A *deprecated feature* is a feature will be cut from the product in a future release, but is still supported and included in the current release to maintain backward compatibility. Typically,  a deprecated feature is removed in a major release, often within two releases of the original  announcement. For example, deprecated features announced in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] are likely to be unsupported by [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
 **Not supported in the next major release of SQL Server**  
  
|||  
|-|-|  
|**Category**|**Feature**|  
|Multidimensional|Remote partitions|  
|Multidimensional|Remote linked measure groups|  
|Multidimensional|Dimensional writeback|  
|Multidimensional|Linked dimensions|  
  
 **Not supported in a future release of SQL Server**  
  
|||  
|-|-|  
|**Category**|**Feature**|  
|Multidimensional|SQL Server table notifications for proactive caching.  <br />The replacement is to use polling for proactive caching. <br />See [Proactive Caching (Dimensions)](assetId:///7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5) and [Proactive Caching (Partitions)](assetId:///422660b2-4d80-4165-b1c9-3963bcde556b).|  
|Multidimensional|Session cubes. There is no replacement.|  
|Multidimensional|Local cubes. There is no replacement.|  
|Tabular|Tabular model 1100 and 1103 compatibility levels will not be supported in a future release. The replacement is to set models at compatibility level 1200, converting model definitions to tabular metadata. See [Compatibility Level for Tabular models in Analysis Services](../../Topics/TopicNameNotContainA/Compatibility-Level-for-Tabular-models-in-Analysis-Services.md).|  
|Tools|SQL Server Profiler for Trace Capture<br /><br /> The replacement is to use Extended Events Profiler embedded in SQL Server Management Studio.  <br /> See [Monitor Analysis Services with SQL Server Extended Events](../../Topics/TopicNameNotContainA/Monitor-Analysis-Services-with-SQL-Server-Extended-Events.md).|  
|Tools|Server Profiler for Trace Replay <br />Replacement. There is no replacement.|  
|Trace Management Objects and Trace APIs|Microsoft.AnalysisServices.Trace objects (contains the APIs for Analysis Services Trace and Replay objects). The replacement is multi-part:<br /><br /> -   Trace Configuration: Microsoft.SqlServer.Management.XEvent<br />-   Trace Reading: Microsoft.SqlServer.XEvent.Linq<br />-   Trace Replay: None|  
  
> [!NOTE]  
>  Previously deprecated feature announcements from [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)] remain in effect. Because the code supporting those features has not yet been cut from the product, many  of these features are still present in this release. While previously deprecated features might be accessible, they are still considered deprecated and could be physically removed from the product at any point during the [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] release. We strongly recommend that you avoid using deprecated features in any new models or applications based on [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
## See Also  
 [Analysis Services Backward Compatibility](../../Topics/TopicNameNotContainA/Analysis-Services-Backward-Compatibility.md)   
 [Discontinued Analysis Services Functionality in SQL Server 2016](../../Topics/TopicNameNotContainA/Discontinued-Analysis-Services-Functionality-in-SQL-Server-2016.md)