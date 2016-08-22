---
title: "What is On-premises Mobile Device Management in System Center Configuration Manager?"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbe331ec-d258-48d9-b460-7e4de39c0d1f
caps.latest.revision: 4
caps.handback.revision: 0
---
# What is On-premises Mobile Device Management in System Center Configuration Manager?
[!INCLUDE[onprem_first](../System Center Configuration Manager/itokens/onprem_first_md.md)] is a device management solution that relies on the built-in management capabilities of device operating systems (based on the Open Mobile Alliance Device Management  or OMA DM standard) while using an enterprise's [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure to manage and maintain the devices. This differs from [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)], which also relies on built-in  OMA DM capabilities, but all of the management functions are delivered through cloud services.  [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] also differs from the client-based management solution traditionally offered by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in that it relies on similar enterprise infrastructure but does not use separately installed client software on the computers and devices it manages.  
  
 The advantages of [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] over traditional client-based management are:  
  
-   Simplified infrastructure - fewer site system roles are required.  
  
-   Easier to maintain - Because management functionality is built-in to the device operating system, new versions of the client software are not required when new management features are introduced to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] system.  
  
-   All management and data kept on-premises.  
  
 Disadvantages:  
  
-   Less client management functionality - No orchestration, software metering, third-party integration, task sequencing, or software center support.  
  
-   Limited device support - currently [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] only supports devices running Windows 10 and Windows 10 Mobile.  
  
## See Also  
 [Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Manage-mobile-devices-with-on-premises-infrastructure-in-System-Center-Configuration-Manager.md)