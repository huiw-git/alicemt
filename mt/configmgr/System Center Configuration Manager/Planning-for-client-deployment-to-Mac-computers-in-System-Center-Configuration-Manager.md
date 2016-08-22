---
title: "Planning for client deployment to Mac computers in System Center Configuration Manager"
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
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
caps.latest.revision: 6
caps.handback.revision: 0
---
# Planning for client deployment to Mac computers in System Center Configuration Manager
You can install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on Mac computers that run the Mac OS X operating system and use the following management capabilities:  
  
-   **Hardware inventory**  
  
     You can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hardware inventory to collect information about the hardware and installed applications on Mac computers. This information can then be viewed in Resource Explorer in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and used to create collections, queries and reports. For more information, see [How to use Resource Explorer to view hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-use-Resource-Explorer-to-view-hardware-inventory-in-System-Center-Configuration-Manager.md).  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collects the following hardware information from Mac computers:  
  
    -   Processor  
  
    -   Computer System  
  
    -   Disk Drive  
  
    -   Disk Partition  
  
    -   Network Adapter  
  
    -   Operating System  
  
    -   Service  
  
    -   Process  
  
    -   Installed Software  
  
    -   Computer System Product  
  
    -   USB Controller  
  
    -   USB Device  
  
    -   CDROM Drive  
  
    -   Video Controller  
  
    -   Desktop Monitor  
  
    -   Portable Battery  
  
    -   Physical Memory  
  
    -   Printer  
  
    > [!IMPORTANT]  
    >  You cannot extend the hardware information that is collected from Mac computers during hardware inventory.  
  
-   **Compliance settings**  
  
     You can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] compliance settings to view the compliance of and remediate Mac OS X preference (.plist) settings. For example, you could enforce settings for the home page in the Safari web browser or ensure that the Apple firewall is enabled. You can also use shell scripts to monitor and remediate settings in MAC OS X.  
  
-   **Application management**  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can deploy software to Mac computers. You can deploy the following software formats to Mac computers:  
  
    -   Apple Disk Image (.DMG)  
  
    -   Meta Package File (.MPKG)  
  
    -   Mac OS X Installer Package (.PKG)  
  
    -   Mac OS X Application (.APP)  
  
 When you install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on Mac computers, you cannot use the following management capabilities that are supported by the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on Windows-based computers:  
  
-   Client push installation  
  
-   Operating system deployment  
  
-   Software updates  
  
    > [!NOTE]  
    >  You can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] application management to deploy required Mac OS X software updates to Mac computers. In addition, you can use compliance settings to make sure that computers have any required software updates.  
  
-   Maintenance windows  
  
-   Remote control  
  
-   Power management  
  
-   Client status client check and remediation  
  
 For more information about how to install and configure the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Mac client, see [How to deploy clients to Macs in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Macs-in-System-Center-Configuration-Manager.md).