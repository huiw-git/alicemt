---
title: "Enroll devices for On-premises Mobile Device Management in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
caps.latest.revision: 6
---
# Enroll devices for On-premises Mobile Device Management in System Center Configuration Manager
To manage computers and devices with [!INCLUDE[onprem_first](../System Center Configuration Manager/itokens/onprem_first_md.md)], the devices need to be enrolled so that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can communicate with the devices for management tasks. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides two methods for enrolling devices:  
  
-   **User enrollment** - In this method, users initiate the enrollment process on their devices. For user enrollment to be successful, the device must have a trusted root certificate installed on it, and the user must be provisioned for enrollment by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  To enroll device, the user simply provides work credentials, and the device is enrolled to be managed.  
  
     For more information, see [How users enroll devices with On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/How-users-enroll-devices-with-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
-   **Bulk enrollment** - In this method, the user of the device is not required to initiate enrollment. Instead a bulk enrollment package created in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and  is then put on the device and opened. When opened, the package provides the information required to enroll the device.  
  
     For more information, see [How to bulk-enroll devices with On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/How-to-bulk-enroll-devices-with-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
 [!INCLUDE[onprem_devices](../System Center Configuration Manager/itokens/onprem_devices_md.md)]   
## See Also  
 [Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Manage-mobile-devices-with-on-premises-infrastructure-in-System-Center-Configuration-Manager.md)