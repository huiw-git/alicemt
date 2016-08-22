---
title: "VPN profiles in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-05-29
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
caps.latest.revision: 6
caps.handback.revision: 0
---
# VPN profiles in System Center Configuration Manager
Use VPN profiles in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to deploy VPN settings to users in your organization. By deploying these settings, you minimize the end-user effort required to connect to resources on the company network.  
  
 For example, you want to provision all devices that run the iOS operating system with the settings required to connect to a file share on the corporate network. You can create a VPN profile containing the settings necessary to connect to the corporate network and then deploy this profile to all users that have devices that run iOS in your hierarchy. Users of iOS devices see the VPN connection in the list of available networks and can connect to this network with the minimum of effort.  
  
 When you create a VPN profile, you can include a wide range of security settings, including certificates for server validation and client authentication that have been provisioned by using [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] certificate profiles. For more information about certificate profiles, see [Certificate profiles in System Center Configuration Manager](../System Center Configuration Manager/Certificate-profiles-in-System-Center-Configuration-Manager.md).  
  
 The sections below explain what devices you can configure with VPN profiles if you are using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with Microsoft Intune.  
  
## VPN profiles when using Configuration Manager  
 The following table describes the VPN profiles you can configure for various device platforms.  
  
|Connection type|Windows 8.1|Windows RT|Windows RT 8.1|Windows 10|  
|---------------------|-----------------|----------------|--------------------|----------------|  
|**Cisco AnyConnect**|No|No|No|No|  
|**Pulse Secure**|Yes|No|Yes|Yes|  
|**F5 Edge Client**|Yes|No|Yes|Yes|  
|**Dell SonicWALL Mobile Connect**|Yes|No|Yes|Yes|  
|**Check Point Mobile VPN**|Yes|No|Yes|Yes|  
|**Microsoft SSL (SSTP)**|Yes|Yes|Yes|No|  
|**Microsoft Automatic**|Yes|Yes|Yes|No|  
|**IKEv2**|Yes|Yes|Yes|No|  
|**PPTP**|Yes|Yes|Yes|No|  
|**L2TP**|Yes|Yes|Yes|No|  
  
## VPN profiles when using Configuration Manager together with Intune  
 To deploy profiles to iOS, Android, Windows Phone, and Windows 8.1 devices, these devices must be enrolled into [!INCLUDE[wit_firstref](../System Center Configuration Manager/itokens/wit_firstref_md.md)]. Devices on other platforms can also be enrolled to [!INCLUDE[wit_nextref](../System Center Configuration Manager/itokens/wit_nextref_md.md)]. For information about how to enroll, see [Manage mobile devices with Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx). This table shows which connection type is supported for each device platform:  
  
|Connection type|iOS    and Mac OS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop and Mobile|  
|---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
|Cisco AnyConnect|Yes|Yes|No|No|No|No|Yes (OMA-URI)|  
|Pulse Secure|Yes|Yes|Yes|No|Yes|Yes|Yes|  
|F5 Edge Client|Yes|Yes|Yes|No|Yes|Yes|Yes|  
|Dell SonicWALL Mobile Connect|Yes|Yes|Yes|No|Yes|Yes|Yes|  
|Check Point Mobile VPN|Yes|Yes|Yes|No|Yes|Yes|Yes|  
|Microsoft SSL (SSTP)|No|No|Yes|Yes|Yes|No|No|  
|Microsoft Automatic|No|No|Yes|Yes|Yes|No|Yes (OMA-URI)|  
|IKEv2|Yes (Custom policy)|No|Yes|Yes|Yes|Yes|Yes (OMA-URI)|  
|PPTP|Yes|No|Yes|Yes|Yes|No|Yes (OMA-URI)|  
|L2TP|Yes|No|Yes|Yes|Yes|No|Yes (OMA-URI)|  
  
## Next steps  
 Use the following topics to help you plan for, configure, operate, and maintain VPN profiles in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   [Prerequisites for VPN profiles in System Center Configuration Manager](../System Center Configuration Manager/Prerequisites-for-VPN-profiles-in-System-Center-Configuration-Manager.md)  
  
-   [Operations and maintenance for VPN profiles in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-VPN-profiles-in-System-Center-Configuration-Manager.md)  
  
-   [Security and privacy for VPN profiles in System Center Configuration Manager](../System Center Configuration Manager/Security-and-privacy-for-VPN-profiles-in-System-Center-Configuration-Manager.md)