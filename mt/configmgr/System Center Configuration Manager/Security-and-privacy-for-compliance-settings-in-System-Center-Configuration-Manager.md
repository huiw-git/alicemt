---
title: "Security and privacy for compliance settings in System Center Configuration Manager"
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
ms.assetid: 1c409244-6778-4970-a99c-d2508c9cf62b
caps.latest.revision: 5
caps.handback.revision: 0
---
# Security and privacy for compliance settings in System Center Configuration Manager
This topic contains security and privacy information for compliance settings in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
## Security best practices for compliance settings  
  
|Security best practice|More information|  
|----------------------------|----------------------|  
|Do not monitor sensitive data.|To help avoid information disclosure, do not configure configuration items to monitor potentially sensitive information.|  
|Do not configure compliance rules that use data that can be modified by end users.|If you create a compliance rule based on data that users can modify, such as registry settings for configuration choices, the compliance results will not be reliable.|  
|Import Microsoft System Center configuration packs and other configuration data from external sources only if they have a valid digital signature from a trusted publisher.|Published configuration data can be digitally signed so that you can verify the publishing source and ensure that the data has not been tampered with. If the digital signature verification check fails, you are warned and prompted to continue with the import. Do not import unsigned data if you cannot verify the source and integrity of the data.|  
|Implement access controls to protect reference computers.|Ensure that when an administrative user configures a registry or file system setting by browsing to a reference computer, the reference computer had not been compromised.|  
|Secure the communication channel when you browse to a reference computer.|To prevent tampering of the data when it is transferred over the network, use Internet Protocol security (IPsec) or server message block (SMB) between the computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and the reference computer.|  
|Restrict and monitor the administrative users who are granted the Compliance Settings Manager role-based security role.|Administrative users who are granted the **Compliance Settings Manager** role can deploy configuration items to all devices and all users in the hierarchy. Configuration items can be very powerful and can include, for example, scripts and registry reconfiguration.|  
  
## Privacy information for compliance settings  
 You can use compliance settings to evaluate whether your client devices are compliant with configuration items that you deploy in configuration baselines. Some settings can be automatically remediated if they out of compliance. Compliance information is sent to the site server by the management point and stored in the site database. The information is encrypted when devices send it to the management point, but it is not stored in encrypted format in the site database. Information is retained in the database until the site maintenance task **Delete Aged Configuration Management Data** deletes it every 90 days. You can configure the deletion interval. Compliance information is not sent to Microsoft.  
  
 By default, devices do not evaluate compliance settings. In addition, you must configure the configuration items and configuration baselines, and then deploy them to devices.  
  
 Before you configure compliance settings, consider your privacy requirements.  
  
## See Also  
 [Compliance settings technical reference for System Center Configuration Manager](../System Center Configuration Manager/Compliance-settings-technical-reference-for-System-Center-Configuration-Manager.md)