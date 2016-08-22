---
title: "What&#39;s new in mobile device management with Configuration Manager and Intune (hybrid)"
ms.custom: na
ms.date: 2016-04-05
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f4d19b2-ce7e-4df2-81e9-62e040850a2d
caps.latest.revision: 11
---
# What&#39;s new in mobile device management with Configuration Manager and Intune (hybrid)
This article provides details on the new mobile device management (MDM) features available for hybrid deployments using [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] and   [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)].  
  
## New MDM features available in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] version 1602  
 The following new MDM features are available in hybrid deployments of [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) version 1602. These features require you to use the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)] to configure and manage them.  
  
### MAM controls to prevent Outlook contacts sync (iOS)  
 A new setting is available for mobile application management without device enrollment. This setting allows you to prevent an application from syncing contacts to the native address book on iOS devices. When this setting is enabled, the app will no longer be able to save contacts to the native address book. When this setting is disabled, the app will be able to save contacts to the native address book. When you selectively wipe a device, all contacts that have already been saved to the native address book will be removed. This new setting is supported by the Outlook application on iOS devices. For more details about this and other settings, see [Protect apps using mobile application management policies in System Center Configuration Manager](../System Center Configuration Manager/Protect-apps-using-mobile-application-management-policies-in-System-Center-Configuration-Manager.md)  
  
### Skype for Business Online supports conditional access  
 You can set a conditional access policy for Skype for Business Online so that it can only be accessed by managed and compliant iOS and Android devices. End users who try to sign in to the Skype for Business mobile app on iOS and Android will be prompted to enroll with Intune as well as fix any non-compliance issues before sign-in can complete. For details, see [Manage Skype for Business Online access](../System Center Configuration Manager/Manage-Skype-for-Business-Online-access.md).  
  
## New MDM features coming soon for hybrid deployments  
 The following new  MDM features are available in hybrid deployments of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] technical preview and will likely be coming to a production version of the current branch in the future.  
  
 [No new MDM features coming soon for hybrid deployments.]  
  
## New MDM features that "just work" in hybrid deployments  
 The following new MDM features work in hybrid deployments exactly as they do in the  standalone [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] service. No changes or administration  in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] are required to use these features.  
  
### [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] support for iOS 9.3  
 On Monday March 21st, Apple announced the availability of iOS 9.3. We have been busy working to ensure that [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] is compatible with the latest version of Apple's mobile operating system, and we are pleased to announce that [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] supports managing iOS 9.3 devices.  
  
 All existing [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] features currently available for managing iOS devices will continue to work seamlessly as users upgrade their devices to iOS 9.3.  
  
### Windows app packages available directly from the Company Portal website  
 Users of Windows 8, Windows 8.1, and Windows RT PCs can now install Windows app packages (with the .appx extension) directly from the Company Portal website. Previously, you had to deploy, or users had to install the Company Portal app on their devices to install apps.  
  
### Users can remotely lock their device from the Company Portal website  
 A new Remote Lock option has been added to the Company Portal website to enable users to remotely lock their device from the Portal if their device is lost or stolen. See the end-user instructions. The following table lists the platform support for Remote Lock.  
  
|Platform|Support details|  
|--------------|---------------------|  
|Android|Supported|  
|iOS|Supported|  
|Windows 10 mobile|Supported only if the phone as a passcode set|  
|Windows 10 desktop|Not supported|  
|Windows Phone 8.1|Supported only if the phone as a passcode set|  
|Windows Phone 8.0|Not supported|  
|Windows 8.1 and earlier|Not supported|