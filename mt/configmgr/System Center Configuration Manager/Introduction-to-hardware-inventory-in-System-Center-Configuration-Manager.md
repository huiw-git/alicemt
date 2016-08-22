---
title: "Introduction to hardware inventory in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
caps.latest.revision: 6
caps.handback.revision: 0
author: barlanmsft
---
# Introduction to hardware inventory in System Center Configuration Manager
Use hardware inventory in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to collect information about the hardware configuration of client devices in your organization. To collect hardware inventory, the **Enable hardware inventory on clients** setting must be enabled in client settings.  
  
 After hardware inventory is enabled and a hardware inventory cycle is run by the client, the client sends the inventory information that it has collected to a management point in the client’s site. The management point then forwards the inventory information to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server which stores the inventory information in the site database. Hardware inventory runs on clients according to the schedule that you specify in client settings.  
  
 You can use several methods to view the hardware inventory data that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collects. These include the following:  
  
-   Create queries that return devices that are based on a specific hardware configuration. For more information, see [Queries technical reference for System Center Configuration Manager](../System Center Configuration Manager/Queries-technical-reference-for-System-Center-Configuration-Manager.md).  
  
-   Create query-based collections that are based on a specific hardware configuration. Query-based collection memberships automatically update on a schedule. You can use collections for several tasks, which include software deployment. For more information, see [Collections technical reference for System Center Configuration Manager](../System Center Configuration Manager/Collections-technical-reference-for-System-Center-Configuration-Manager.md).  
  
-   Run reports that display specific details about hardware configurations in your organization. For more information, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
-   Use Resource Explorer to view detailed information about the hardware inventory that is collected from client devices. For more information, see [How to use Resource Explorer to view hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-use-Resource-Explorer-to-view-hardware-inventory-in-System-Center-Configuration-Manager.md).  
  
 When hardware inventory runs on a client device, the first inventory data that the client returns is always a full inventory. Subsequent inventory information contains only delta inventory information. The site server processes delta inventory information in the order in which it is received. If delta inventory information for a client is missing, the site server rejects additional delta inventory information and instructs the client to run a full inventory cycle.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides limited support for dual-boot computers. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can discover dual-boot computers but only returns inventory information from the operating system that was active at the time the inventory cycle ran.  
  
> [!NOTE]  
>  For information about how to use hardware inventory with clients that run Linux and UNIX, see [Hardware inventory for Linux and UNIX in System Center Configuration Manager](../System Center Configuration Manager/Hardware-inventory-for-Linux-and-UNIX-in-System-Center-Configuration-Manager.md).  
  
## Extending Configuration Manager hardware inventory  
 In addition to the built-in hardware inventory in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can also use one of the following methods to extend hardware inventory to collect additional information:  
  
|Method|Description|  
|------------|-----------------|  
|Add and remove inventory classes from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console|In [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can enable, disable, add and remove inventory classes for hardware inventory from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.|  
|NOIDMIF files|Use NOIDMIF files to collect information about client devices that cannot be inventoried by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For example, you might want to collect device asset number information that exists only as a label on the device. NOIDMIF inventory is automatically associated with the client device that it was collected from.|  
|IDMIF files|Use IDMIF files to collect information about assets in your organization that are not associated with a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, for example, projectors, photocopiers and network printers.|  
  
 For more information about using these methods to extend [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hardware inventory, see [How to configure hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-hardware-inventory-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/Hardware-inventory-in-System-Center-Configuration-Manager.md)