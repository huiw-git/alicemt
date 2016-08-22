---
title: "Choose a device management solution for System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
caps.latest.revision: 14
caps.handback.revision: 0
---
# Choose a device management solution for System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] offers different solutions for managing PCs, servers, and devices. You can choose the solution that’s right for you based on the device platforms you need to manage and the management functionality you need.  
  
 In this article:  
  
-   [Overview of device management solutions](#bkmk_overview)  
  
-   [Compare device management solutions based on supported mobile device platforms](#bkmk_comp1)  
  
-   [Compare mobile device management solutions based on management functionality](#bkmk_comp2)  
  
##  <a name="bkmk_overview"></a> Overview of device management solutions  
 The following options are available to manage computers and  devices with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
  
-   **Managing devices with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client**  
  
     This option, which requires installation of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client application on each device to be managed, provides the most features and functionality for managing PCs, servers, and other devices in your environment. This option is the traditional way [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] has provided device management over the history of the product.  
  
     For more information about this solution, see [Manage computer clients with System Center Configuration Manager](../System Center Configuration Manager/Manage-computer-clients-with-System-Center-Configuration-Manager.md).  
  
-   **Managing mobile devices with on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure**  
  
     This option uses the device management capabilities built into operating systems of certain device platforms. While not as full-featured as the client-based management, [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] provides a lighter touch approach to management that uses on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] resources to reach and manage devices. [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] is currently only supported for Windows 10 PCs and Windows 10 Mobile devices.  
  
     For more information about this solution, see [Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Manage-mobile-devices-with-on-premises-infrastructure-in-System-Center-Configuration-Manager.md).  
  
-   **Managing mobile devices with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] (hybrid)**  
  
     This option is referred to as hybrid mobile device management.  It uses [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] to enroll and manage devices instead of using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] on-premises resources. Even though [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] manages the devices, you to control management tasks in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. This option supports all major mobile device operating systems, including Windows 10 Mobile, Windows Phone, iOS, and Android. It also provides management for Windows 8.1 and Windows 10 computers in your organization.  
  
     For more information about this solution, see [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).  
  
-   **Managing mobile devices with Exchange**  
  
     This option, which uses the Exchange Server connector to connect to multiple Exchange servers to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], centralizes management of devices that can connect to Exchange ActiveSync. You can configure Exchange mobile device management features, such as remote device wipe and settings control for multiple Exchange servers, from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
     For more information about this solution, see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md)  
  
 You can use these device management solutions by themselves are in combination with each other. For example, you can use the client-based management approach to cover managing the computers and servers in your organization and also use Intune-based management to cover mobile devices. By combining approaches in this way, you can cover all of your device management needs and control it all from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
##  <a name="bkmk_comp1"></a> Compare device management solutions based on supported mobile device platforms  
  
|Platform|With the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] (hybrid)|[!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)]|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with Exchange|  
|--------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Android||Yes||Yes|  
|iOS||Yes||Yes|  
|Mac OS X|Yes|||Yes|  
|UNIX/Linux|Yes|||Yes|  
|Windows 10|Yes|Yes|Yes|Yes|  
|Windows 10 Mobile||Yes|Yes|Yes|  
|Windows(previous versions)|Yes|Yes||Yes|  
|Windows CE|Yes (with mobile device legacy client)|||Yes|  
|Windows Embedded|Yes||||  
|Windows Phone||Yes||Yes|  
|Windows Server|Yes|||Yes|  
  
 For a complete list of support platforms, see the following sections in [Supported operating systems for sites and clients for System Center Configuration Manager](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md):  
  
-   [Supported operating systems for System Center Configuration Manager Clients](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md#bkmk_ClientOS)  
  
-   [Mobile devices enrolled by Microsoft Intune](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md#bkmk_IntuneOS)  
  
-   [On-premises mobile device management](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md#bkmk_OnpremOS)  
  
##  <a name="bkmk_comp2"></a> Compare mobile device management solutions based on management functionality  
  
|Management functionality|With the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] (hybrid)|[!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)]|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with Exchange|  
|------------------------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Public key infrastructure (PKI) security between the mobile device and Configuration Manager by using mutual authentication and SSL to encrypt data transfers|Yes|Yes|Yes||  
|Client installation|Yes||||  
|Support over the Internet|Yes||||  
|Discovery|Yes|||Yes|  
|Hardware inventory|Yes|Yes|Yes|Yes|  
|Software inventory|Yes|||Yes|  
|Settings|Yes|Yes|Yes|Yes|  
|Software deployment|Yes|Yes|Yes||  
|Monitor with fallback status point|Yes||||  
|Connections to management points|Yes||Yes||  
|Connections to distribution points|Yes|Yes|Yes||  
|Block from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]|Yes|Yes|Yes||  
|Quarantine and block from Exchange Server (and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)])||||Yes|  
|Remote wipe|Yes|Yes|Yes|Yes|  
  
## See Also  
 [Manage computers and devices with System Center Configuration Manager](../System Center Configuration Manager/Manage-computers-and-devices-with-System-Center-Configuration-Manager.md)