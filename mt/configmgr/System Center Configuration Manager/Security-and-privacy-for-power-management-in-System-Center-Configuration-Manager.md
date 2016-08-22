---
title: "Security and privacy for power management in System Center Configuration Manager"
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
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
caps.latest.revision: 5
caps.handback.revision: 0
---
# Security and privacy for power management in System Center Configuration Manager
This section contains security and privacy information for power management in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
## Security best practices for power management  
 There are no security-related best practices for power management.  
  
## Privacy information for power management  
 Power management uses features that are built into Windows to monitor power usage and to apply power settings to computers during business hours and nonbusiness hours. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collects power usage information from computers, which includes data about when a user is using a computer. Although [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] monitors power usage for a collection rather than for each computer, a collection can contain just one computer. Power management is not enabled by default and must be configured by an administrator.  
  
 The power usage information is stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database and is not sent to Microsoft. Detailed information is retained in the database for 31 days and summarized information is retained for 13 months. You cannot configure the deletion interval.  
  
 Before you configure power management, consider your privacy requirements.  
  
## See Also  
 [Power management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Power-management-technical-reference-for-System-Center-Configuration-Manager.md)