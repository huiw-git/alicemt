---
title: "About the service connection point in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-06-27
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
caps.latest.revision: 18
caps.handback.revision: 0
---
# About the service connection point in System Center Configuration Manager
The [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] service connection point is a site system role that serves several important functions for the hierarchy. Before configuring the service connection point, understand and plan for its range of uses which might affect how you configure this site system role:  
  
-   **Manage mobile devices with Microsoft Intune** – This role replaces the Windows Intune connector  used by previous versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], and can be configured with your [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription details. See [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md)  
  
-   **Manage mobile devices with on-premises MDM** – This role provides support for on-premises devices you manage that do not connect to the Internet. See [Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Manage-mobile-devices-with-on-premises-infrastructure-in-System-Center-Configuration-Manager.md)  
  
-   **Upload usage data from your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure** – You can control the level or amount of detail you upload. Uploaded data helps us:  
  
    -   Proactively identify and troubleshoot problems  
  
    -   Improve our products and service  
  
    -   Identify updates for Configuration Manager that apply to the version of Configuration Manager you use  
  
     See [Usage data levels and settings](../System Center Configuration Manager/Reference-for-System-Center-Configuration-Manager-Setup.md#bkmk_usage).  
  
-   **Download updates that apply to your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure** – Only relevant updates for your infrastructure are made available, based on usage data you upload.  
  
 **Each hierarchy supports a single instance of this role:**  
  
-   The site system role can only be installed at the top-tier site of your hierarchy (A central administration site or the stand-alone primary site).  
  
-   If you expand a stand-alone primary site into a larger hierarchy, you must uninstall this role from the primary site and can then install it at the central administration site.  
  
##  <a name="bkmk_modes"></a> Modes of operation  
 The service connection point supports two modes of operation:  
  
-   In **online mode**, the service connection point automatically checks every 24 hours for updates and then downloads new updates that are available for your current infrastructure and product version, making them available in the Configuration Manager console  
  
-   In **offline mode**, the service connection point does not connect to the Microsoft cloud service and you must manually [Use the Service Connection Tool for System Center Configuration Manager](../System Center Configuration Manager/Use-the-Service-Connection-Tool-for-System-Center-Configuration-Manager.md) to import available updates  
  
 When you change the mode between online or offline after you have installed the service connection point, you  must then restart the SMS_DMP_DOWNLOADER thread of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SMS_Executive service before this change becomes effective.  To do this, use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Service Manager to restart only the SMS_DMP_DOWNLOADER thread of the SMS_Execctuive service.  You can also restart the the SMS_Executive service for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (which restarts most site components), or wait for a schedule task like a site backup which stops and then later restarts the SMS_Executive for you.  
  
 To use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Service Manager, in the console navigate to **Monitoring** > **System Status** > **Component Status**, click **Start**, and then   select **Configuration Manager Service Manager**.  In the service manager:  
  
-   In the navigation pane, expand the  site and then **Components**, and then select the component you want to restart.  
  
-   In the details pane, right click on the component and select **Query**.  
  
-   After the status of the component is confirmed, right click on the component again, and select **Stop**.  
  
-   **Query** the component again, to confirm it is stopped, and then right click on the component one more time, and select **Start**.  
  
> [!IMPORTANT]  
>  When you add a  [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] subscription to the service connection point, it automatically sets the site system role to be online. The service connection point does not support offline mode when configured with a [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription.  
  
 **When the role installs on a computer that is remote from the site server:**  
  
-   You must configure the site system server that hosts the role with a Site System Installation Account  
  
-   The Site System Installation Account is used by the distribution manager on the site server to transfer updates from the service connection point.  
  
##  <a name="bkmk_urls"></a> Internet access requirements  
 To enable operation, the computer that hosts the service connection point and any firewalls between that computer and the Internet must pass communications through **port TCP 443** to the following Internet locations. The service connection point also supports using a web proxy (with or without authentication) to access these locations.  
  
 **Updates and Servicing**  
  
-   *.akamaiedge.net  
  
-   *.manage.microsoft.com 

-   go.microsoft.com 
  
-   blob.core.windows.net  
  
-   download.microsoft.com  
  
-   sccmconnected-a01.cloudapp.net  
  
 **Microsoft Intune**  
  
-   *manage.microsoft.com  
  
 **Windows 10 Servicing**  
  
-   download.microsoft.com  
  
-   https://go.microsoft.com/fwlink/?LinkID=619849  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)