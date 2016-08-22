---
title: "Set up Android hybrid device management with System Center Configuration Manager and Microsoft Intune"
ms.custom: na
ms.date: 2016-06-29
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: c517fe34-0130-465b-a020-bdb555878778
caps.latest.revision: 9
caps.handback.revision: 0
---
# Set up Android hybrid device management with System Center Configuration Manager and Microsoft Intune
For [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], users can download the Android company portal app from Google Play that lets them enroll Android (including Samsung KNOX) devices. With the Android company portal app, you can manage compliance settings, wipe or delete Android devices, deploy apps, and collect software and hardware inventory. If the Android company portal app is not installed on Android devices, then you will not have all the management capabilities, such as inventory and compliance settings, but you can still deploy apps to Android devices.  
  
## Prepare to manage Android mobile devices with Configuration Manager and Intune  
 The following steps allow [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to manage Android devices.  
  
#### To enable Android enrollment  
  
1.  **Prerequisites** - Before you can set up enrollment for any platform, complete the prerequisites and procedures in [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).  
  
2.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console in the **Administration** workspace, go to **Cloud Services** > **Microsoft Intune Subscription**.  
  
3.  On the **Home** tab in the **Subscription** group, click **Configure Platforms** > **Android**.  
  
4.  In the **Microsoft Intune Subscription Properties** dialog box, select the **Android** tab and click to select the **Enable Android enrollment** checkbox.  
  
 Once you're set up, you'll need to let your users know how to enroll their devices. See [What to tell users about enrolling their devices](https://technet.microsoft.com/library/dn948527.aspx). This information applies to both Microsoft Intune and Configuration Manager-managed mobile devices.