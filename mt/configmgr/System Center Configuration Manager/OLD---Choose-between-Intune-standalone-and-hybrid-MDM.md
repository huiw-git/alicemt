---
title: "OLD - Choose between Intune standalone and hybrid MDM"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59531eb7-cf4e-41c8-a806-2f7096fd18d7
caps.latest.revision: 4
---
# OLD - Choose between Intune standalone and hybrid MDM
Use the information in this article to compare the capabilities of two different mobile device management (MDM) solutions:  
  
-   [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] standalone.  
  
-   Hybrid MDM, which uses [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] to manage mobile devices as part of the overall [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] deployment.  
  
|You might choose [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] standalone if:|You might choose hybrid MDM with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] if:|  
|------------------------------------------------------------|----------------------------------------------------------------|  
|You want to manage mobile devices.<br /><br /> You want to manage computers that are not joined to a domain.<br /><br /> You have fewer than 50,000 devices to manage.<br /><br /> You have no (or limited) on-premises IT infrastructure.<br /><br /> [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] does not require on-premises IT infrastructure, however it can use the capabilities of Exchange ActiveSync or Active Directory Domain Services if you have those installed.<br /><br /> You have a mobile or highly distributed workforce. Cloud-based device management lets you manage mobile devices and computers anywhere in the world.|You want to manage computers joined to a domain.<br /><br /> You want to manage servers.<br /><br /> You want to manage computers with the Configuration Manager client, Mac computers, Linux and UNIX server, and mobile devices enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] from the same console.<br /><br /> You have more than 50,000 devices to manage.<br /><br /> You have on-premises IT infrastructure in place, or plan to deploy such infrastructure. In this configuration, the device and resource management experience is fully unified.<br /><br /> User names and passwords are synchronized, providing users with a single account that they use to access company resources, whether from a domain-joined computer or from a mobile device.|  
  
## Detailed comparison of capabilities  
 The following tables compare the device and app management capabilities available to you when you use [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] alone, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] alone, or a hybrid solution that uses both products.  
  
### Device support  
  
|Platform|[!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] standalone|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] standalone|Hybrid MDM  ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)])|  
|--------------|---------------------------------------|--------------------------------------|-----------------------------------------------------------------------|  
|Microsoft Windows|Yes|Yes|Yes|  
|Microsoft Windows Server|No|Yes|Yes|  
|Windows Phone|Yes|No|Yes|  
|Windows RT|Yes|No|Yes|  
|iOS|Yes|No|Yes|  
|Android and Samsung KNOX|Yes|No|Yes|  
|Mac OS X|Yes|Yes|Yes|  
|UNIX/Linux servers|No|Yes|Yes|  
  
### Product capabilities  
  
|Scenario|[!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] standalone|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] standalone|Hybrid MDM  ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)])|  
|--------------|---------------------------------------|--------------------------------------|-----------------------------------------------------------------------|  
|**Compliance settings**||||  
|Deploy and customize Windows PC device configuration settings (e.g., WMI, registry)|No|Yes|Yes|  
|Deploy and customize Mac OS X configuration settings|Yes|Yes|Yes|  
|Deploy configuration settings to mobile devices|Yes|Yes|Yes|  
|Deploy custom mobile device settings (such as OMA-URI and Apple Configurator)|Yes|Yes|Yes|  
|**Deployment**||||  
|Deploy apps to devices and Windows PCs|Yes|Yes|Yes|  
|Deploy Windows operating systems|No|Yes|Yes|  
|**Security and privacy**||||  
|Manage Windows software updates|Yes|Yes|Yes|  
|Monitor malware on Windows PCs with Endpoint Protection|Yes|Yes|Yes|  
|**Administration and reporting**||||  
|Monitor and report on how often software is being used with software metering|No|Yes|Yes|  
|Hardware and software inventory|Yes|Yes|Yes|  
|Extend hardware and software inventory for Windows PCs|No|Yes|Yes|  
|Use role-based administration and reporting to control who has access to product capabilites|No|Yes|Yes|  
|Run reports for Windows PCs and enrolled mobile devices from the same console|No|No|Yes|  
|Customize existing reports, and write your own reports using SQL Server Reporting Services|No|Yes|Yes|  
|**Data protection for mobile devices**||||  
|Deploy security settings to mobile devices|Yes|Yes|Yes|  
|Remote wipe|Yes|Yes|Yes|  
|Remote lock|Yes|Yes|Yes|  
|Passcode reset|Yes|Yes|Yes|  
|**Company resource access**||||  
|Email profiles|Yes|Yes|Yes|  
|Wi-Fi profiles|Yes|Yes|Yes|  
|VPN profiles|Yes|Yes|Yes|  
|Certificate profiles|Yes|Yes|Yes|  
|Manage access to Exchange email and SharePoint with conditional access|Yes|Yes|Yes|  
|Mobile application management|Yes|Yes|Yes|  
|App compliance policies (compliant and noncompliant apps)|Yes|Yes|Yes|  
|Kiosk mode|Yes|Yes|Yes|  
|Managed Internet browser policy|Yes|Yes|Yes|  
|**Automation**||||  
|Use PowerShell to automate operations|No|Yes|Yes|