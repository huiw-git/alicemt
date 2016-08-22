---
title: "Diagnostics and usage data for System Center Configuration Manager"
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
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: 9
caps.handback.revision: 0
---
# Diagnostics and usage data for System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] collects diagnostics and usage data about itself which is used by Microsoft to improve the installation experience, quality, and security of future releases.  
  
 Diagnostics  and Usage Data is enabled for each [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy. It consists of SQL Server queries that run on a weekly basis on each primary site and at central administration site. When the hierarchy uses a central administration site, the data from primary sites is then replicated to that site. At the top-level site of your hierarchy, the service connection point submits this information when it checks for updates. If the service connection point is in offline mode, the information is transferred by using the service connection tool.  
  
> [!NOTE]  
>  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] only collects data from the sites SQL server database, and does not collect data directly from clients or site servers.  
  
 For more information see the [Privacy Statement for System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626527).  
  
 Learn more about diagnostic and usage data for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] in the following topics:  
  
-   [How diagnostics and usage data is used for System Center Configuration Manager](../System Center Configuration Manager/How-diagnostics-and-usage-data-is-used-for-System-Center-Configuration-Manager.md)  
  
-   [Levels of diagnostic usage data collection for System Center Configuration Manager](../System Center Configuration Manager/Levels-of-diagnostic-usage-data-collection-for-System-Center-Configuration-Manager.md)  
  
-   [How diagnostics and usage data is collected by System Center Configuration Manager](../System Center Configuration Manager/How-diagnostics-and-usage-data-is-collected-by-System-Center-Configuration-Manager.md)  
  
-   [How to view diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/How-to-view-diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)  
  
-   [Customer Experience Improvement Program (CEIP) for System Center Configuration Manager](../System Center Configuration Manager/Customer-Experience-Improvement-Program--CEIP--for-System-Center-Configuration-Manager.md)  
  
-   [Frequently asked questions about diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/Frequently-asked-questions-about-diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Technical reference for System Center Configuration Manager](../System Center Configuration Manager/Technical-reference-for-System-Center-Configuration-Manager.md)   
 [Site installation technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md)   
 [About the service connection point in System Center Configuration Manager](../System Center Configuration Manager/About-the-service-connection-point-in-System-Center-Configuration-Manager.md)