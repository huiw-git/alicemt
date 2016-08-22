---
title: "Creating iOS applications with System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-16
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: d5420109-6538-4430-9ca6-db352ee84c2e
caps.latest.revision: 10
author: barlanmsft
---
# Creating iOS applications with System Center Configuration Manager
In addition to the other [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] requirements and procedures for creating an application, you must also take the following considerations into account when you create and deploy applications for iOS devices.  
  
## General considerations  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports deploying the following app types:  
  
|Device Type|Supported Files|  
|-----------------|---------------------|  
|iOS|*.ipa<br /><br /> In [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you do not need to specify a property list (.plist) file when importing an iOS app.|  
  
 The following deployment actions are supported:  
  
|Device type|Supported actions|  
|-----------------|-----------------------|  
|iOS|Available, Required (though user must consent to the install), Uninstall|  
  
> [!IMPORTANT]  
>  Currently, end-users cannot install corporate apps from the Microsoft Intune Company Portal app for iOS. This is due to restrictions placed on apps that are published in the iOS App Store (see App Store Review Guidelines, Section 2). Users can install corporate apps (including managed App Store apps and line-of-business app packages) by browsing to the Intune Web Portal on their device (portal.manage.microsoft.com). For more information about the mobile management capabilities enabled by the Intune Company Portal app, see [Mobile device management capabilities in Microsoft Intune](https://technet.microsoft.com/library/dn600287.aspx).  
  
## See Also  
 [Deploy and manage applications with System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-applications-with-System-Center-Configuration-Manager.md)