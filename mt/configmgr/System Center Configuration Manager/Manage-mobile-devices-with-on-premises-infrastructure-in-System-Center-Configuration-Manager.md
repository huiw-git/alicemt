---
title: "Manage mobile devices with on-premises infrastructure in System Center Configuration Manager"
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
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
caps.latest.revision: 8
---
# Manage mobile devices with on-premises infrastructure in System Center Configuration Manager
[!INCLUDE[onprem_first](../System Center Configuration Manager/itokens/onprem_first_md.md)] is a device management solution that relies on the built-in management capabilities of device operating systems (based on the Open Mobile Alliance Device Management  or OMA DM standard) while using an enterprise's [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure to manage and maintain the devices. [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] requires [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] to set up the management capability, but it's only needed for the subscription (and at times to help notify devices to check in for policy changes), but it's not used to manage devices or store data about them.  
  
 ![On&#45;premises conceptual](../System Center Configuration Manager/medias/On-premises-conceptual.png "On-premises)  
  
 [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] differs from [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)], which also relies on built-in  OMA DM capabilities, but all of the management functions are delivered through cloud services.  [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] also differs from the client-based management solution traditionally offered by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in that it relies on similar enterprise infrastructure but does not use separately installed client software on the computers and devices it manages.  
  
 The table below lists the advantages and disadvantages of [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] as compared to traditional client-based management:  
  
|Advantages|Disadvantages|  
|----------------|-------------------|  
|**Simplified infrastructure** - Fewer site system roles are required.<br /><br /> **Easier to maintain** - Because management functionality is built-in to the device operating system, new versions of the client software are not required when new management features are introduced to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] system.<br /><br /> **On-premises** - All management and data kept on-premises.|**Less client management functionality** - No orchestration, software metering, third-party integration, task sequencing, or software center support.<br /><br /> **Limited device support** - currently [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] only supports devices running Windows 10 and Windows 10 Mobile.|  
  
 The following topics provides information you can use to plan, prepare, and enroll devices for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)]:  
  
-   [Plan for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
     Learn about what to consider when setting up the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure and planning for device enrollment in [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)].  
  
-   [Preparation steps for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Preparation-steps-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
     Learn about how to get the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] system ready for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] by setting up the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] subscription, setting up certificates, installing site system roles, and setting up device enrollment.  
  
-   [Enroll devices for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Enroll-devices-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
     Learn about how enrollment occurs, how users can enroll their own devices, and how to bulk-enroll devices with an enrollment package.  
  
## See Also  
 [Manage computers and devices with System Center Configuration Manager](../System Center Configuration Manager/Manage-computers-and-devices-with-System-Center-Configuration-Manager.md)