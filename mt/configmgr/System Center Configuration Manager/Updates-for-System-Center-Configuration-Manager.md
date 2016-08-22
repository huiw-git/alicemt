---
title: "Updates for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
caps.latest.revision: 51
caps.handback.revision: 0
---
# Updates for System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] uses an in-console service method called **Updates and Servicing** that makes it easy to locate and then install recommended updates for your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure. This in-console servicing method is supplemented by out-of-band updates such as hotfixes that are intended for customers who need to resolve issues that might be specific to their environment.  
  
 **The following topics can help you understand how to find and install the different update types for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:**  
  
-   [Install in-console updates for System Center Configuration Manager](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md)  
  
-   [Use the Service Connection Tool for System Center Configuration Manager](../System Center Configuration Manager/Use-the-Service-Connection-Tool-for-System-Center-Configuration-Manager.md)  
  
-   [Use the Update Registration Tool to import hotfixes to System Center Configuration Manager](../System Center Configuration Manager/Use-the-Update-Registration-Tool-to-import-hotfixes-to-System-Center-Configuration-Manager.md)  
  
-   [Use the Hotfix Installer to install updates for System Center Configuration Manager](../System Center Configuration Manager/Use-the-Hotfix-Installer-to-install-updates-for-System-Center-Configuration-Manager.md)  
  
 
##  <a name="bkmk_Baselines"></a> Baseline and update versions  
 The initial release of System Center Configuration Manager current branch is version 1511. This is a baseline version:  
  
-   Use the latest baseline version when you install a new site in a new hierarchy.  
  
-   You must use a baseline version to upgrade from System Center 2012 Configuration Manager.  
  
-   Periodically, new baseline versions will be released. When you use a newer baseline version to install a new hierarchy you avoid installing the original 1511 baseline followed by an upgrade of your infrastructure.  
  
 After you install a baseline version, additional versions of Configuration Manager are available as in-console updates. In-console updates update your infrastructure to the latest version of Configuration Manager.  
  
-   You install in-console updates to update the version of your top-level site.  
  
-   Updates you install at central administration site will automatically install at child primary sites, unless blocked by a maintenance window you have configured at the primary site.  
  
-   You must manually update secondary sites to a new update version from within the console.  
  
 When you install an update, the update stores installation files for that version on the site server in a folder named CD.Latest. See [The CD.Latest folder for System Center Configuration Manager](../System Center Configuration Manager/The-CD.Latest-folder-for-System-Center-Configuration-Manager.md) for more information about these files.  
  
-   You use the files in the CD.Latest folder during site recovery and to install additional sites in a hierarchy that no longer runs a baseline version.  
  
-   You cannot use installation files from CD.Latest to install the first site of a new hierarchy, or to upgrade a site from System Center 2012 Configuration Manager.  
  
 Some updates for Configuration Manager are available as both an in-console update version for existing infrastructure, and as a new baseline version.  
  
 The following versions of Configuration Manager are available as a baseline, an update, or both:  
  
|Version|Availability date|Baseline|in-console update|  
|-------------|-----------------------|--------------|------------------------|  
|**1511**<br /><br /> 5.00.8325.1000|12/8/2015|Yes|No|  
|**1602**<br /><br /> 5.00.8355.1000|3/11/2016|No|Yes|
|**1606**<br /><br /> 5.00.8412.1000|7/22/2016|No|Yes| 
  
 To check the version of your Configuration Manager site, in the console go to **About System Center Configuration Manager** at the top-left corner of the console where the new site and console version displays.  
  
##  <a name="bkmk_inconsole"></a> In-console updates and servicing  
 When you use a production ready installation of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], also referred to as the current branch, the majority of updates you install are available using the Updates and Servicing channel. This method identifies, downloads, and makes available the updates that apply to your current infrastructure version and configuration, and includes only updates that Microsoft recommends for all customers.   
 These include:  
  
-   New versions, like version 1602  
  
-   Updates, that include new features for your current version  
  
-   Hotfixes, for your version of Configuration Manager and that all customers should install  
  
 The in-console updates deliver increased stability and resolve common issues. They replace the update types seen for previous product versions for service packs, cumulative updates, hotfixes that are applicable to all customers,  and Extension for Microsoft Intune. These updates can apply to one or more of the following:  
  
-   Primary and central administration site servers  
  
-   Site system roles and site system servers  
  
-   Instances of the SMS Provider  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients  
  
 Configuration Manager discovers new updates for you when you synchronize your service connection point site system role with the Microsoft cloud service and download center:  
  
-   When your service connection point is in online mode, your site synchronizes with Microsoft every day to automatically identify new updates that apply to your infrastructure.  To download updates and redist files for updates, the computer that hosts the Service Connection Point site system role uses the **System** context to  access the following Internet locations: go.microsoft.com and download.microsoft.com. For information about additional locations the service connection point connects to, see [Internet access requirements](../System Center Configuration Manager/About-the-service-connection-point-in-System-Center-Configuration-Manager.md#bkmk_urls) in [About the service connection point in System Center Configuration Manager](../System Center Configuration Manager/About-the-service-connection-point-in-System-Center-Configuration-Manager.md).  
  
-   When your service connection point is in offline mode, you use the service connection tool to manually sync with the Microsoft cloud. For more information, see [Use the Service Connection Tool for System Center Configuration Manager](../System Center Configuration Manager/Use-the-Service-Connection-Tool-for-System-Center-Configuration-Manager.md).  
  
-   In-console updates replace the need to independently locate and install individual updates, service packs, and new features.  
  
-   You install only the in-console updates you choose, and when installing some updates you can select the individual features you want to enable and use. For more information, see [Enable optional features from updates](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md#bkmk_options).  
  
 When you install an in-console update:  
  
-   It automatically runs a prerequisite check. You can also run this check prior to starting the installation.  
  
-   It installs at the central administration site (if you have one), and at primary sites automatically. You can control when each primary site server is allowed to update its infrastructure by using [Service Windows for site servers](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md#bkmk_ServiceWindow).  
  
-   After a site server updates, all affected site system roles (including instances of the SMS Provider) automatically update. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles also prompt the console user to update the console, after the site installs the update.  
  
-   If an update includes the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, you are offered the option to test the update in pre-production, or to apply the update to all clients immediately.  
  
-   After a primary site is updated, secondary sites do not automatically update. Instead, you must initiate the secondary site update.  
  
> [!NOTE]  
>  The production release of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] (current branch) and the Technical Preview for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] are different releases. Therefore, updates for the current branch release are never available in or for the Technical Preview for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].    Similarly, updates for the Technical Preview are not available in the current branch release.  
  
##  <a name="bkmk_outofband"></a> Out-of-band hotfixes  
 Some hotfixes are released with limited availability to address specific issues, or are applicable to all customers but cannot be installed using the in-console method. These fixes are delivered out-of-band and not discovered from the Microsoft cloud service.  
  
 Typically, you learn about out-of-band hotfixes from Microsoft customer support services, a Knowledge Base article, or from the [System Center Configuration Manager Team blog](https://blogs.technet.microsoft.com/configmgrteam) when you are seeking to fix or address a problem with your deployment of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 You install these fixes manually, using one of two methods:  
  
-   **Update Registration Tool:** This tool manually imports the hotfix into your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console where you can then install the update as you would in-console updates that are discovered automatically. This method is used for updates that use the following file name structure: **.update.exe**.  The full file name for this type of hotfix resembles: **<Product\>-<product version\>-<KB article ID\>-ConfigMgr.Update.exe**  
  
     For more information, see [Use the Update Registration Tool to import hotfixes to System Center Configuration Manager](../System Center Configuration Manager/Use-the-Update-Registration-Tool-to-import-hotfixes-to-System-Center-Configuration-Manager.md)  
  
-   **Hotfix Installer:** This tool is used to manually install a hotfix that cannot be installed using the in-console method. This method is used for fixes that use the following file name structure: **<Product\>-<product version\>-<KB article ID\>-<platform\>-<language\>.exe**  
  
     For more information, see [Use the Hotfix Installer to install updates for System Center Configuration Manager](../System Center Configuration Manager/Use-the-Hotfix-Installer-to-install-updates-for-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Monitor and maintain System Center Configuration Manager](../System Center Configuration Manager/Monitor-and-maintain-System-Center-Configuration-Manager.md)