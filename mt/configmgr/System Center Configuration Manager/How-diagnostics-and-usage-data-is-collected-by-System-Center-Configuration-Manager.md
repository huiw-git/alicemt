---
title: "How diagnostics and usage data is collected by System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
caps.latest.revision: 5
---
# How diagnostics and usage data is collected by System Center Configuration Manager
To collect diagnostics and usage data for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], each primary site runs SQL Server queries on a weekly basis. In a multi-site hierarchy, the data is replicated to the central administration site.  
  
 At the top-level site of a hierarchy, the service connection point site system role submits this information when it checks for updates. How the data transfers depends on the mode of the service connection point:  
  
-   **In online mode:** Diagnostics and usage data is automatically sent once a week from the service connection point to the cloud service.  
  
-   **In offline mode:** Diagnostics and usage data is transferred manually by using the service connection tool. For more information, see [Use the Service Connection Tool for System Center Configuration Manager](../System Center Configuration Manager/Use-the-Service-Connection-Tool-for-System-Center-Configuration-Manager.md).  
  
 For more information, see [About the service connection point in System Center Configuration Manager](../System Center Configuration Manager/About-the-service-connection-point-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/Diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)   
 [Levels of diagnostic usage data collection for System Center Configuration Manager](../System Center Configuration Manager/Levels-of-diagnostic-usage-data-collection-for-System-Center-Configuration-Manager.md)   
 [How diagnostics and usage data is used for System Center Configuration Manager](../System Center Configuration Manager/How-diagnostics-and-usage-data-is-used-for-System-Center-Configuration-Manager.md)   
 [How to view diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/How-to-view-diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)