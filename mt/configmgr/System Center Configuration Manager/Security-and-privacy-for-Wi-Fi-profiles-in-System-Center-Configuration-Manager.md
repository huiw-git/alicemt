---
title: "Security and privacy for Wi-Fi profiles in System Center Configuration Manager"
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
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
caps.latest.revision: 4
caps.handback.revision: 0
---
# Security and privacy for Wi-Fi profiles in System Center Configuration Manager
This topic contains security and privacy information for Wi-Fi profiles in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
##  <a name="BKMK_Security_RemoteConnections"></a> Security Best Practices for Wi-Fi Profiles  
 Use the following security best practices when you manage Wi-Fi profiles for devices.  
  
|Security best practice|More information|  
|----------------------------|----------------------|  
|Whenever possible, choose the most secure options that your Wi-Fi infrastructure and client operating systems can support.|Wi-Fi profiles provide a convenient method to centrally distribute and manage Wi-Fi settings that your devices already support. [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] does not add Wi-Fi functionality.<br /><br /> Identify, implement, and follow any security best practices that have been recommended for your devices and Wi-Fi infrastructure.|  
  
## Privacy Information for Wi-Fi Profiles  
 You can use Wi-Fi profiles to configure client devices to connect to Wi-Fi servers, and then evaluate whether those devices become compliant after the profiles are applied. The management point sends compliance information to the site server, and the information is stored in the site database. The information is encrypted when devices send it to the management point, but it is not stored in encrypted format in the site database. The database retains the information until the site maintenance task **Delete Aged Configuration Management Data** deletes it. The default deletion interval is 90 days, but you can change it. Compliance information is not sent to Microsoft.  
  
 By default, devices do not evaluate Wi-Fi profiles. In addition, you must configure the VPN profiles, and then deploy them to users.  
  
 Before you configure Wi-Fi profiles, consider your privacy requirements.  
  
## See Also  
 [Wi-Fi Profiles in System Center Configuration Manager](../System Center Configuration Manager/Wi-Fi-Profiles-in-System-Center-Configuration-Manager.md)