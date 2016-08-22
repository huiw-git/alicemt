---
title: "Fundamentals of client management tasks for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-04-18
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
caps.latest.revision: 4
---
# Fundamentals of client management tasks for System Center Configuration Manager
After you have installed [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] clients, there are several tasks you can run to manage the clients.  Some you  start from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console while other can be started or viewed on a  client from the clients [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] app in the Windows control panel.  
  
## The console  
 From within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you can perform various client management tasks, which include the following:  
  
-   Deploy applications, software updates, maintenance scripts, and operating systems. You can configure these to be installed by a specified date and time, or make them available for users to install when they are requested, and you can configure applications to be uninstalled.  
  
-   Help protect computers from malware and security threats, and notify you when problems are detected.  
  
-   Define client configuration settings that you want to monitor and remediate if they are out of compliance.  
  
-   Collect hardware and software inventory information, which includes monitoring and reconciling license information from Microsoft.  
  
-   Troubleshoot computers by using remote control.  
  
-   Implement power management settings to manage and monitor the power consumption of computers.  
  
 To monitor these operations in near real-time, you use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to view alerts and status information. To capture data and historical trending, you can use the integrated reporting capabilities of SQL Reporting Services.  Clients submit details to the site as client status.  Client status  information  provides data about the health of the client and client activity and can be viewed in the console or by using built-in reports for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. This data helps identify computers that are not responding and in some cases, problems can be automatically remediated.  
  
 For more information about  management tasks for clients, see  [How to manage clients in System Center Configuration Manager](../System Center Configuration Manager/How-to-manage-clients-in-System-Center-Configuration-Manager.md) and [How to manage clients for Linux and UNIX servers in System Center Configuration Manager](../System Center Configuration Manager/How-to-manage-clients-for-Linux-and-UNIX-servers-in-System-Center-Configuration-Manager.md). To learn about using reports, see   
            [Introduction to reporting in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-reporting-in-System-Center-Configuration-Manager.md).  
  
## The Windows control panel app  
 When you install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client software, this installs the **Configuration Manager** client application in Control Panel. Unlike Software Center, this application is designed for the help desk rather than for end users. Some configuration options require local administrative permissions and most options require technical knowledge about how [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] works. You can use this application to perform the following tasks on a client:  
  
-   View properties about the client, such as the build number, its assigned site, the management point it is communicating with, and whether the client is using a PKI certificate or a self-signed certificate.  
  
-   Confirm that the client has successfully downloaded client policy after the client is installed for the first time and that client settings are enabled or disabled as expected, according to the client settings that are configured in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
-   Start client actions, such as download the client policy if there was a recent change of configuration in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and you do not want to wait until the next schedule time.  
  
-   Manually assign a client to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site or try to find a site, and specify the DNS suffix for management points that publish to DNS.  
  
-   Configure the client cache that temporarily stores files, and delete files in the cache if you require more disk space to install software.  
  
-   Configure settings for Internet-based client management.  
  
-   View configuration baselines that were deployed to the client, initiate compliance evaluation, and view compliance reports.  
  
## See Also  
 [Fundamentals of System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-System-Center-Configuration-Manager.md)