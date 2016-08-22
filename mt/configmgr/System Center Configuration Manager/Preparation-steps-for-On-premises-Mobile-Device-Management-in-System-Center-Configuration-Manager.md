---
title: "Preparation steps for On-premises Mobile Device Management in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
caps.latest.revision: 4
---
# Preparation steps for On-premises Mobile Device Management in System Center Configuration Manager
Managing devices with [!INCLUDE[onprem_first](../System Center Configuration Manager/itokens/onprem_first_md.md)] requires the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure to be set up so that the required site system roles (enrollment proxy point, enrollment point, device management point, and distribution point) can communicate across a trusted channel with the mobile devices to be managed.  
  
 The following high-level tasks are required to prepare the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] system for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)]:  
  
-   [Set up a Microsoft Intune subscription for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Set-up-a-Microsoft-Intune-subscription-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
     In this task, you sign up for [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)], and then add the subscription to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] through the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. This step is required for licensing purposes only. [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] is not used to manage the devices or store management information. All coordination and management of devices is with your organization's enterprise using the on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure.  
  
-   [Install site system roles for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Install-site-system-roles-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
     In this task, you install and configure the site system roles required to manage devices with on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure. [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] minimally requires the enrollment proxy point, enrollment point, device management point, and distribution point site system roles.  
  
-   [Set up certificates for trusted communications for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Set-up-certificates-for-trusted-communications-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
     In this task, you configure the on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure to allow trusted communications (HTTPS) between managed devices and the servers hosting the required site system roles.  
  
-   [Set up device enrollment for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Set-up-device-enrollment-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
     In this task, you grant permission to users to enroll computers and devices and you install the trusted root certificate on devices (typically ones that are not domain-joined) to permit HTTPS connections to the site system servers.  
  
## See Also  
 [Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Manage-mobile-devices-with-on-premises-infrastructure-in-System-Center-Configuration-Manager.md)