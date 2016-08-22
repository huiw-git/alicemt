---
title: "Considerations for monitoring clients in System Center Configuration Manager"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 79f90efe-06f1-459b-bf91-7df71e6183f5
caps.latest.revision: 6
caps.handback.revision: 0
---
# Considerations for monitoring clients in System Center Configuration Manager
Use the **Client Status** node in the **Monitoring** workspace of the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console to monitor the health and activity of client computers in your hierarchy. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses the following two methods to evaluate the overall status of client computers.  
  
 **Client Activity**: You can configure thresholds to determine whether a client is active, for example:  
  
-   Whether the client requested policy during the last seven days.  
  
-   Whether Heartbeat Discovery found the client during the last seven days.  
  
-   Whether the client sent hardware inventory during the last seven days.  
  
 When all these thresholds are exceeded, the client is determined to be inactive.  
  
 **Client Check**: A client evaluation engine is installed with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, which periodically evaluates the health of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client and its dependencies. This engine can check or remediate some problems with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
 On computers that run Windows 7, client check runs as a scheduled task. On later operating systems, client check runs automatically during the Windows maintenance window.  
  
 You can configure remediation not to run on specific computers, for example, a business-critical server. In addition, if there are additional items that you want to evaluate, you can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] compliance settings to provide a comprehensive solution to monitor the overall health, activity, and compliance of computers in your organization. For more information about compliance settings, see [Plan for and configure compliance settings in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-and-configure-compliance-settings-in-System-Center-Configuration-Manager.md).  
  
 Client status uses the monitoring and reporting capabilities of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to provide information in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console about the health and activity of the client. You can configure alerts to notify you when clients check results or client activity drops below a specified percentage of clients in a collection or when remediation fails on a specified percentage of clients.  
  
 For information about how to configure client status, see [How to configure client status in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-status-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_ClientHealth"></a> Checks and remediations made by client check  
 The following checks and remediations can be performed by client check.  
  
|Client check|Remediation action|More information|  
|------------------|------------------------|----------------------|  
|Verify that client check has recently run|Run client check|Checks that client check has run at least one time in the past three days.|  
|Verify that client prerequisites are installed|Install the client prerequisites|Checks that client prerequisites are installed. Reads the file ccmsetup.xml in the client installation folder to discover the prerequisites.|  
|WMI repository integrity test|Reinstall the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client|Checks that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client entries are present in WMI.|  
|Verify that the client service is running|Start the client (SMS Agent Host) service|No additional information|  
|WMI Event Sink Test.|Restart the client service|Check whether the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] related WMI event sink is lost|  
|Verify that the Windows Management Instrumentation (WMI) service exists|No remediation|No additional information|  
|Verify that the client was installed correctly|Reinstall the client|No additional information|  
|WMI repository read and write test|Reset the WMI repository and reinstall the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client|Remediation of this client check is only performed on computers that run Windows Server 2003, Windows XP (64-bit) or earlier versions.|  
|Verify that the antimalware service startup type is automatic|Reset the service startup type to automatic|No additional information|  
|Verify that the antimalware service is running|Start the antimalware service|No additional information|  
|Verify that the Windows Update service startup type is automatic or manual|Reset the service startup type to automatic|No additional information|  
|Verify that the client service (SMS Agent Host) startup type is automatic|Reset the service startup type to automatic|No additional information|  
|Verify that the Windows Management Instrumentation (WMI) service is running.|Start the Windows Management Instrumentation service|No additional information|  
|Verify that the Microsoft SQL CE database is healthy|Reinstall the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client|No additional information|  
|Microsoft Policy Platform WMI Integrity Test|Repair the Microsoft Policy Platform|No additional information|  
|Verify that the Microsoft Policy Platform Service exists|Repair the Microsoft Policy Platform|No additional information|  
|Verify that the Microsoft Policy Platform service startup type is manual|Reset the service startup type to manual|No additional information|  
|Verify that the Background Intelligent Transfer Service exists|No Remediation|No additional information|  
|Verify that the Background Intelligent Transfer Service startup type is automatic or manual|Reset the service startup type to automatic|No additional information|  
|Verify that the Network Inspection Service startup type is manual|Reset the service startup type to manual if installed|No additional information|  
|Verify that the Windows Management Instrumentation (WMI) service startup type is automatic|Reset the service startup type to automatic|No additional information|  
|Verify that the Windows Update service startup type on Windows 8 computers is automatic or manual|Reset the service startup type to manual|No additional information|  
|Verify that the client (SMS Agent Host) service exists.|No Remediation|No additional information|  
|Verify that the Configuration Manager Remote Control service startup type is automatic or manual|Reset the service startup type to automatic|No additional information|  
|Verify that the Configuration Manager Remote Control service is running|Start the remote control service|No additional information|  
|Verify that the client WMI provider is healthy|Restart the Windows Management Instrumentation service|Remediation of this client check is only performed on computers that run Windows Server 2003, Windows XP (64-bit) or earlier.|  
|Verify that the wake-up proxy service (ConfigMgr Wake-up Proxy) is running|Start the ConfigMgr Wakeup Proxy service|This client check is made only if the **Power Management**: **Enable wake-up proxy** client setting is set to **Yes** on supported client operating systems.|  
|Verify that the wake-up proxy service (ConfigMgr Wake-up Proxy) startup type is automatic|Reset the ConfigMgr Wakeup Proxy service startup type to automatic|This client check is made only if the **Power Management**: **Enable wake-up proxy** client setting is set to **Yes** on supported client operating systems.|