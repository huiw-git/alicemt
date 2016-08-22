---
title: "Introduction to software inventory in System Center Configuration Manager"
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
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
caps.latest.revision: 5
caps.handback.revision: 0
author: barlanmsft
---
# Introduction to software inventory in System Center Configuration Manager
Use software inventory in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to collect information about files that are contained on client devices in your organization. Additionally, software inventory can collect files from client devices and store these on the site server. Software inventory is collected when the **Enable software inventory on clients** setting is enabled in client settings.  
  
 After software inventory is enabled and the clients run a software inventory cycle, the client sends the inventory information to a management point in the client’s site. The management point then forwards the inventory information to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server, which stores the inventory information in the site database. Software inventory runs on clients according to the schedule that you specify in client settings.  
  
 You can use a number of methods to view the software inventory data that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collects. These include the following:  
  
-   Create queries that return devices that are based on files you specify that are found on devices. For more information, see [Queries technical reference for System Center Configuration Manager](../System Center Configuration Manager/Queries-technical-reference-for-System-Center-Configuration-Manager.md).  
  
-   Create query-based collections that are based on files you specify that are found on devices. Query-based collection memberships automatically update on a schedule. You can use collections for a number of tasks such as software deployment. For more information, see [Collections technical reference for System Center Configuration Manager](../System Center Configuration Manager/Collections-technical-reference-for-System-Center-Configuration-Manager.md).  
  
-   Run reports that display specific details about files on devices in your organization. For more information, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
-   Use Resource Explorer to examine detailed information about the files that were inventoried and collected from client devices. For more information, see [How to use Resource Explorer to view software inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-use-Resource-Explorer-to-view-software-inventory-in-System-Center-Configuration-Manager.md).  
  
 When software inventory runs on a client device, the first inventory report returned is always a full inventory. Subsequent inventory reports contain only delta inventory information. The site server processes delta inventory information in the order in which it is received. If delta inventory information for a client is missing, the site server rejects further delta inventory information and instructs the client to run a full inventory cycle.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides limited support for dual-boot computers. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can discover dual-boot computers but only returns inventory information from the operating system that was active at the time of inventory.  
  
## Software inventory for mobile devices enrolled with Microsoft Intune  
 You can collect inventory on apps installed on mobile devices. The apps that are inventoried will depend on whether the device is company-owned or personal-owned. For personal devices, the only apps that are inventoried are apps that are managed by [!INCLUDE[wit_firstref](../System Center Configuration Manager/itokens/wit_firstref_md.md)].  
  
> [!NOTE]  
>  Inventory on the apps installed on mobile devices is collected as part of the hardware inventory process in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For more information, see [How to configure hardware inventory for mobile devices enrolled by Microsoft Intune and System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-hardware-inventory-for-mobile-devices-enrolled-by-Microsoft-Intune-and-System-Center-Configuration-Manager.md).  
  
 The table below lists what apps are inventoried for personal-owned or company-owned devices.  
  
|Platform|For Personal-owned Devices|For Company-owned devices|  
|--------------|---------------------------------|--------------------------------|  
|Windows 8.1 (without the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client)|Only managed apps|Only managed apps|  
|Windows Phone 8|Only managed apps|Only managed apps|  
|Windows RT|Only managed apps|Only managed apps|  
|iOS|Only managed apps|All apps installed on the device|  
|Android|Only managed apps|All apps installed on the device|  
  
## See Also  
 [Software inventory in System Center Configuration Manager](../System Center Configuration Manager/Software-inventory-in-System-Center-Configuration-Manager.md)