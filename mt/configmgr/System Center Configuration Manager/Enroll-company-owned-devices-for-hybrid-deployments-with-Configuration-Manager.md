---
title: "Enroll company-owned devices for hybrid deployments with Configuration Manager"
ms.custom: na
ms.date: 2016-07-27
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: e2754ce6-1460-4ddd-9050-2cc87e7964f4
caps.latest.revision: 13
---
# Enroll company-owned devices for hybrid deployments with Configuration Manager
Organization or corporate-owned devices (COD) can be brought into management in a variety of ways depending upon the device and how it was purchased.  
  
## Enroll Device Enrollment Program iOS devices  
 Deploys an enrollment profile “over the air” to devices purchased through Apple's Device Enrollment Program. When the user runs Setup Assistant on the device, the device is enrolled in Intune.  Devices enrolled through DEP cannot be un-enrolled by users. See [iOS Device Enrollment Program (DEP) enrollment for hybrid deployments with Configuration Manager](../System Center Configuration Manager/iOS-Device-Enrollment-Program--DEP--enrollment-for-hybrid-deployments-with-Configuration-Manager.md).  
  
## Enroll iOS devices with Apple Configurator  
 This method requires the administrator to USB connect the iOS device to a Mac computer running Apple Configurator to preconfigure the enrollment. Devices are then delivered to their users who run the Setup Assistant process, configuring the device with their work or school credentials and completing the enrollment process. See [iOS hybrid enrollment using Apple Configurator with Configuration Manager](../System Center Configuration Manager/iOS-hybrid-enrollment-using-Apple-Configurator-with-Configuration-Manager.md).  
  
## Device Enrollment Manager  
 Organizations can use Intune to manage large numbers of mobile devices with a single user account called a device enrollment manager account. After creating a device enrollment manager account, that account can be used by a manager to enroll more than the standard five devices allowed by default to normal users. Enrolling devices with a device enrollment manager only works for devices that aren't used by a specific user. These devices are good for point-of-sale or utility apps, for example, but bad for users who need access to email or company resources. See [Enroll devices with device enrollment manager with Configuration Manager](../System Center Configuration Manager/Enroll-devices-with-device-enrollment-manager-with-Configuration-Manager.md).  
  
## User affinity for managed devices  
 When configuring profiles for corporate-owned devices, the administrator can specify whether the managed devices support *user affinity* which identifies a specific user with the device. Devices configured with **user affinity** can install and run the Company Portal app to download apps and manage devices. See [User affinity for hybrid managed devices in Configuration Manager](../System Center Configuration Manager/User-affinity-for-hybrid-managed-devices-in-Configuration-Manager.md).  
  
## Manage devices with Activation Lock  
 Microsoft Intune can help you manage iOS Activation Lock, a feature of the Find My iPhone app for iOS 7.1 and later devices. Activation Lock is enabled automatically when the Find My iPhone app is used on a device. See [Manage iOS Activation Lock with System Center Configuration Manager](../System Center Configuration Manager/Manage-iOS-Activation-Lock-with-System-Center-Configuration-Manager.md). 
 
 ## Predeclare devices with IMEI or iOS serial numbers
 
You can identify corporate-owned devices by importing their international station mobile equipment identity (IMEI) numbers or iOS serial numbers. You can upload a comma-separated values (.csv) file containing device IMEI numbers or you can manually enter device information.  See [Predeclare devices with IMEI or iOS serial numbers](../System Center Configuration Manager/Predeclare-devices-with-IMEI-or-iOS-serial-numbers.md).
  
## See Also  
 [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md)