---
title: "How to monitor clients in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 2c8f57cf-1968-48de-87fb-4897432ed6e0
caps.latest.revision: 23
---
# How to monitor clients in System Center Configuration Manager

In this article:  
[About client status](#bkmk_about)  
[Monitor the status of individual clients](#bkmk_indStatus)  
[Monitor the status of all clients](#bkmk_allStatus)  
[Checks and remediations made by client check](#BKMK_ClientHealth)
  
 Once the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] client application has been installed on the Windows computers and devices in your site, you can monitor their health and activity in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
##  <a name="bkmk_about"></a> About client status  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides the following types of information as client status:  
  
-   **Client online status** - Beginning in version 1602 of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], this status indicates if the computer is online or not. A computer is considered online if it is connected to it's assigned management point.  To indicate that the client is online, it sends ping-like messages to the management point. If the management point doesn't receive a message in 5 minutes or so, the client is considered offline.  
  
-   **Client activity** - This status indicates if the client has been actively engaging with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] over the last 7 days. If the client hasn't requested a policy update, sent a heartbeat message, or sent hardware inventory in 7 days, the client is considered inactive.  
  
-   **Client check** - This status indicates the success of the periodic evaluation that the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client runs on the computer.  The evaluation checks the computer and can remediate some of the problems it finds. For more information, see [Checks and remediations made by client check](#BKMK_ClientHealth).  
  
     On computers that run Windows 7, client check runs as a scheduled task. On later operating systems, client check runs automatically during the Windows maintenance window.  
  
     You can configure remediation not to run on specific computers, for example, a business-critical server. In addition, if there are additional items that you want to evaluate, you can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] compliance settings to provide a comprehensive solution to monitor the overall health, activity, and compliance of computers in your organization. For more information about compliance settings, see [Plan for and configure compliance settings in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-and-configure-compliance-settings-in-System-Center-Configuration-Manager.md).  
  
##  <a name="bkmk_indStatus"></a> Monitor the status of individual clients  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance** > **Devices** or choose a collection under **Device Collections**.  
  
     Beginning in version 1602 of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)],  the icons at the beginning of each row indicate the online status of the device:  
  
    |||  
    |-|-|  
    |![online status icon for clients](../System Center Configuration Manager/medias/online-status-icon.png "online)|Device is online.|  
    |![offline status icon for clients](../System Center Configuration Manager/medias/offline-status-icon.png "offline)|Device is offline.|  
    |![unknown status icon for clients](../System Center Configuration Manager/medias/unknown-status-icon.png "unknown)|Online status is unknown.|  
    |![client not installed](../System Center Configuration Manager/medias/client-not-installed.png "client)|Client is not installed on device.|  
  
2.  For more detailed online status, add the client online status information to the device view by right-clicking the column header and clicking the online status fields you want to add. The columns you can add are  
  
    -   **Device Online Status** indicates whether the client is currently online or offline. (This is the same information given by the icons).  
  
    -   **Last Online Time** indicates when the client online status changed to online.  
  
    -   **Last Offline Time** indicates when the status changed to offline.  
  
3.  Click an individual client in the list pane to see more status in the detail pane including information about client activity and client checks.  
  
##  <a name="bkmk_allStatus"></a> Monitor the status of all clients  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring** > **Client Status**. On this page of the console, you can review the overall statistics for client activity and client checks across the site.  You can also change the scope of the information by choosing a different collection.  
  
2.  To drill down into detail about the reported statistics, click the name of the reported information (such as **Active clients that have passed client check or no results**) and review the information about the individual clients.  
  
3.  Click **Client Activity** to see charts depicting the client activity in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
4.  Click **Client Check** to see charts depicting the status of client checks in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
 You can configure alerts to notify you when clients check results or client activity drops below a specified percentage of clients in a collection or when remediation fails on a specified percentage of clients. For information about how to configure client status, see [How to configure client status in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-status-in-System-Center-Configuration-Manager.md).  
  
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
  
## See Also  
 [How to monitor clients for Linux and UNIX servers in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-clients-for-Linux-and-UNIX-servers-in-System-Center-Configuration-Manager.md)   
 [Monitor and manage clients in System Center Configuration Manager](../System Center Configuration Manager/Monitor-and-manage-clients-in-System-Center-Configuration-Manager.md)