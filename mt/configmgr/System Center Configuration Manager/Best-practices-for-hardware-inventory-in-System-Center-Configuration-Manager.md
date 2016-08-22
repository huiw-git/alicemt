---
title: "Best practices for hardware inventory in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: daed49d1-060c-4511-9cfe-3890d396ae68
caps.latest.revision: 5
caps.handback.revision: 0
author: barlanmsft
---
# Best practices for hardware inventory in System Center Configuration Manager
Use the following best practices information to help you use hardware inventory in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
## Enable MIF file collection only when required  
 MIF files could contain large amounts of data and collecting this data could negatively affect the performance of your site. Enable MIF file collection only when required and configure the option **Maximum custom MIF file size (KB)** in the hardware inventory client settings. For more information, see [How to extend hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-extend-hardware-inventory-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Planning for hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-hardware-inventory-in-System-Center-Configuration-Manager.md)