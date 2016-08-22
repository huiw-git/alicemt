---
title: "Determine the site system roles for System Center Configuration Manager clients"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
caps.latest.revision: 9
caps.handback.revision: 0
---
# Determine the site system roles for System Center Configuration Manager clients
Use the following sections to help you determine the site systems that you require to deploy [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients:  
  
-   [Determine Whether You Require a Management Point](#BKMK_Determine_MP)  
  
-   [Determine Whether You Require a Fallback Status Point](#BKMK_Determine_FSP)  
  
-   [Determine Whether You Require an Enrollment Point and an Enrollment Proxy Point](#BKMK_Determine_EnrollmentPoints)  
  
-   [Determine Whether You Require a Distribution Point](#BKMK_Determine_DP)  
  
-   [Determine Whether You Require an Application Catalog Website Point and an Application Catalog Web Services Point](#BKMK_Determine_ApplicationCatalogPoints)  
  
 For more information about where to install these site system roles in the hierarchy, see [Design a hierarchy of sites for System Center Configuration Manager](../System Center Configuration Manager/Design-a-hierarchy-of-sites-for-System-Center-Configuration-Manager.md).  
  
 For more information about how to install and configure the site system roles that you require, see [Install site system roles](../System Center Configuration Manager/Install-site-system-roles-for-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_Determine_MP"></a> Determine Whether You Require a Management Point  
 By default, all Windows client computers use a distribution point to install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client and can fall back to a management point when a distribution point is not available. However, you can install Windows clients on computers from an alternative source when you use the CCMSetup command-line property **/source:<Path\>**. For example, this might be appropriate if you install clients on the Internet. Another scenario is when you want to avoid sending network packets between the computer and the management point during client installation, perhaps because a firewall blocks the ports required for your installation method or because you have a low-bandwidth connection. However, all clients must communicate with a management point to assign to a site, and to be managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 For more information about the CCMSetup command-line property **/source:<Path\>**, see [About client installation properties in System Center Configuration Manager](../System Center Configuration Manager/About-client-installation-properties-in-System-Center-Configuration-Manager.md).  
  
 When you install more than one management point in the hierarchy, clients automatically connect to the most appropriate one, based on their forest membership and network location. You cannot install more than one management point in a secondary site.  
  
 Mac computer clients and mobile device clients that you enroll with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] always require a management point for client installation. This management point must be in a primary site, must be configured to support mobile devices, and must accept client connections from the Internet. These clients cannot use management points in secondary sites or connect to management points in other primary sites.  
  
##  <a name="BKMK_Determine_FSP"></a> Determine Whether You Require a Fallback Status Point  
 You can use a fallback status point to monitor client deployment for Windows computers and identify the clients on these computers that are unmanaged because they cannot communicate with a management point. Mac computers, mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], and mobile devices that are managed by using the Exchange Server connector do not use a fallback status point.  
  
> [!NOTE]  
>  A fallback status point is not required to monitor client activity and client health.  
  
 The fallback status point always communicates with clients by using HTTP, which uses unauthenticated connections and sends data in clear text. This makes the fallback status point vulnerable to attack, particularly when it is used with Internet-based client management. To help reduce the attack surface, always dedicate a server to running the fallback status point and do not install other site system roles on the same server in a production environment.  
  
 Install a fallback status point if all the following conditions apply:  
  
-   You want client communication errors from Windows computers to be sent to the site, even if these client computers cannot communicate with a management point.  
  
-   You want to use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client deployment reports, which display the data that is sent by the fallback status point.  
  
-   You have a dedicated server for this site system role and have additional security measures to help protect the server from attack.  
  
-   The benefits of using a fallback status point outweigh any security risks associated with unauthenticated connections and clear text transfers over HTTP traffic.  
  
 Do not install a fallback status point if the following condition applies:  
  
-   The security risks of running a website with unauthenticated connections and clear text transfers outweigh the benefits of identifying client communication problems.  
  
##  <a name="BKMK_Determine_RSP"></a> Determine Whether You Require a Reporting Services Point  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides many reports to help you monitor the installation, assignment, and management of clients in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. Some of the client deployment reports require that clients are assigned to a fallback status point.  
  
 Although the reports are not required to deploy clients and you can see some deployment information in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console or use the client log files for detailed information, the client reports provide valuable information to help monitor and troubleshoot client deployment.  
  
##  <a name="BKMK_Determine_EnrollmentPoints"></a> Determine Whether You Require an Enrollment Point and an Enrollment Proxy Point  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] requires the enrollment point and the enrollment proxy point to enroll mobile devices and to enroll certificates for Mac computers. These site system roles are not required if you will manage mobile devices by using the Exchange Server connector, or if you install the mobile device legacy client (for example, for Windows CE), or if you request and install the client certificate on Mac computers independently from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
##  <a name="BKMK_Determine_DP"></a> Determine Whether You Require a Distribution Point  
 Although you don’t require a distribution point to install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients on Windows computers, by default, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses a distribution point to install the client source files on Windows computers but can fall back to downloading these files from a management point. Distribution points are not used to install mobile device clients that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] but are used if you install the mobile device legacy client. If you install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client as part of an operating system deployment, the operating system image is stored and retrieved from a distribution point.  
  
 Although you might not require distribution points to install most [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients, you will require distribution points to install software such as applications and software updates on the clients.  
  
##  <a name="BKMK_Determine_ApplicationCatalogPoints"></a> Determine Whether You Require an Application Catalog Website Point and an Application Catalog Web Services Point  
 The Application Catalog website point and the Application Catalog web service point are not required for client deployment. However, you might want to install them as part of your client deployment process, so that users can perform the following actions as soon as the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is installed on Windows computers:  
  
-   Wipe their mobile devices.  
  
-   Search for and install applications from the Application Catalog.  
  
-   Deploy applications to users and devices with a deployment purpose of **Available**.  
  
## See Also  
 [Planning considerations for deploying clients in System Center Configuration Manager](../System Center Configuration Manager/Planning-considerations-for-deploying-clients-in-System-Center-Configuration-Manager.md)