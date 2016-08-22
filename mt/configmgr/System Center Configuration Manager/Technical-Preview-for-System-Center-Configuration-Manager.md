---
title: "Technical Preview for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-19
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 157
---
# Technical Preview for System Center Configuration Manager
**Welcome to the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Technical Preview**. This topic provides details about the evolving preview release that introduces new functionality and capabilities we are working on. With each version of the technical preview, new features are introduced that are not included in the current branch of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] at the time the technical preview version is made available. These features might eventually be included in an update to the current branch release, but before we finalize the features and add them, we want you to have a chance to try them out and give us feedback.  
  
 Because this is a technical preview, details and functionality are subject to change.  
  
 This topic contains information that applies to all versions of the Technical Preview, and also  lists each new capability (or feature) along with the  Technical Preview version in which the capability first appears, like version 1512 for December of 2015. The details for these capabilities are detailed in  separate topics dedicated to each preview version.  
  
 For information about what's new in the current branch of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [What's new in System Center Configuration Manager](What%E2%80%99s%20new%20in%20System%20Center%20Configuration%20Manager%20incremental%20versions.md).
  
> [!NOTE]  
>  For information about what's in System Center Configuration Manager Technical Preview 4 (and earlier previews), see [Technical Previews for the pre-release of System Center Configuration Manager](https://technet.microsoft.com/library/dn965439.aspx)  
  
 **In this topic:**  
  
-   [Requirements and limitations for the Technical Preview](#bkmk_reqs)  
  
-   [Install and update the Technical Preview](#bkmk_install)  
  
-   [Providing feedback](#BKMK_TPFeedback)  
  
-   [General changes introduced in Technical Previews](#bdmk_tpknownissues)  
  
-   [Capabilities delivered in technical previews](#bkmk_tpCaps)  
  
##  <a name="bkmk_reqs"></a> Requirements and limitations for the Technical Preview  
  
> [!IMPORTANT]  
>  The Technical Preview is licensed for use only in a lab environment.  Microsoft may not provide support services and certain features may not be available in the Preview software. Additionally, the Preview software may have reduced or different security, privacy, accessibility, availability and reliability standards relative to commercially provided software.  
  
 For most product prerequisites, use the information in the [!INCLUDE[cm6long] (../Token/cm6long_md.md)] [Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md). The following exceptions apply to the Technical Preview releases:  
  
-   Each install remains active for 90 days before it becomes inactive.  
  
-   English is the only language supported.  
  
-   Only a stand-alone primary site is supported. There is no support for a central administration site, multiple primary sites, or secondary sites.  
  
-   Only the following versions of SQL Server are supported:  
  
    -   SQL Server 2012 with cumulative update 2 or later  
  
    -   SQL Server 2014  
  
-   The site supports up to 10 clients, which must run one of the following:  
  
    -   Windows 7  
  
    -   Windows 8  
  
    -   Windows 8.1  
  
    -   Windows 10  
  
-   Only the following install flags (switches) are supported:  
  
    -   **/silent**  
  
    -   **/testdbupgrade**  
  
-   When applicable, additional limitations or requirements are included with details for each specific version of the Technical Preview  
  
-   There is no support for migration to or from this preview build.  
  
-   There is no support for upgrade to this preview build.  
  
-   There is no support for upgrade to a production build (current branch) from this preview build. However, when updates are available for a preview version,  you can find and install them from the **Updates and Servicing** node of the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)]. For a video of the in-console upgrade process, see [Installing ConfigMgr Update Packages](https://www.youtube.com/embed/KBd_EGFbUT8) on youtube.com.  
  
##  <a name="bkmk_install"></a> Install and update the Technical Preview  
 The [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Technical Preview is distinct from the current release of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
 To use the technical preview you must first install a **baseline version** of the technical preview build. After installing a baseline version, you then use **in-console updates** to bring your installation up to date with the most recent preview version.     Typically, new versions of the Technical Preview are available each month.  
  
> [!TIP]  
>  When you install  an update to the  technical preview, you  update your preview installation to that new technical preview version.    A technical preview installation  never has the option to upgrade to a current branch installation, nor  receive updates from the current branch release.  
  
 **Active baseline versions of the Technical Preview:**  
  
-   **Technical Preview 1603** as part of the **System Center Technical Preview 5** -  The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview 1603  is available as both an in-console update for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview, and as a new baseline version that is included with System Center Technical Preview 5.    Only the version included with System Center Technical Preview 5 can be used for a baseline install.  
  
     About  the baseline version of the [Configuration Manager Technical Preview from System Center Technical Preview 5](https://www.microsoft.com/en-us/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview):  
  
    -   Both Setup and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console list the version as the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Technical Preview 1603.  
  
    -   This baseline version functions as does the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview 1603, including support for in-console updates.  
  
    -   You can install this baseline version for up to 9 months after the release of System Center Technical Preview 5.  
  
    -   You can run this baseline version for 90 days before you must update it to a later version. (Typically, versions of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview run for 60 days before you must update them to a later version.)  
  
##  <a name="BKMK_TPFeedback"></a> Providing feedback  
 We would love to hear your feedback about our technical previews. To submit feedback about the capabilities in each preview, follow the link to our feedback form on the [Configuration Manager feedback program](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) page on the Microsoft Connect site.  
  
 And, if you have ideas about new features you would like to see, we want to know that as well. To submit new ideas and to vote on the ideas submitted by others, [visit our user voice page](http://configurationmanager.uservoice.com).  
  
##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews  
  
-   **Technical Preview 1601:** By default, the service connection point is set to online mode when it installs, and does not support a change to offline mode.  
  
-   **Technical Preview 1602:** Beginning with Technical Preview 1602, you can in-place upgrade the operating system of a site system server that runs Windows 2008 Server R2 to Windows 2012 Server R2.  When you use the Windows Server 2012 R2 upgrade procedures, you do not need to run a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server restore after the upgrade.  For upgrade procedures, see [Upgrade Options for Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx).  
  
    > [!WARNING]  
    >  Before you upgrade to Windows Server 2012 R2, **you must uninstall WSUS 3.2** from the server.  
    >   
    >  For information about this critical step, see the New and changed functionality section  in [Windows Server Update Services Overview](https://technet.microsoft.com/library/hh852345.aspx) in the Windows Server documentation.  
  
-   **Technical Preview 1603:**  
  
    -   Beginning with Technical Preview 1603, you can configure software updates deployments to have clients run a software updates compliance scan immediately after a client installs software updates and restarts. This enables the client to check for additional software updates that become applicable after the client restarts, and to then install them (and become compliant) during the same maintenance window.  
  
         To configure this for a deployment, on the **User Experience** page of the Deploy Software Updates Wizard select the option **If any update in this deployment requires a system restart, run updates deployment evaluation cycle after restart**.  
  
    -   Beginning with Technical Preview 1603, the behavior for the SMSTSRebootDelay task sequence variable has changed. The  SMSTSRebootDelay variable specifies how many seconds to wait before the computer restarts. The task sequence manager will display a notification dialog before the restart if this variable is not set to 0.  
        When you configure a value for this variable, that value will persist until you configure a new value. The delay for all the subsequent computer restarts will have the same value. In [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] version 1602 and earlier, the variable is reset to the default value (30 seconds) after the computer restarts.   For more information, see [Task sequence built-in variables in System Center Configuration Manager](../System Center Configuration Manager/Task-sequence-built-in-variables-in-System-Center-Configuration-Manager.md).  
  
##  <a name="bkmk_tpCaps"></a> Capabilities delivered in technical previews  
 The following are the  capabilities delivered  with each [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] technical preview release.  Capabilities that are available beginning in a version of the technical preview remain available in later versions. Similarly, capabilities that have been added to the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Release (current branch) remain  available in subsequent technical previews.  Click through to the content for each preview version to learn more about a specific capability.  
  
|Capability|Available beginning in|  
|----------------|----------------------------|  
|[Integration with Windows Update for Business in Windows 10](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1511-for-System-Center-Configuration-Manager.md#BKMK_WUfB)|[1511](https://technet.microsoft.com/library/mt706225.aspx)|  
|[Managing Office 365 ProPlus Client Update through System Center Configuration Manager](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1511-for-System-Center-Configuration-Manager.md#BKMK_Office365ProPlus)|[1511](https://technet.microsoft.com/library/mt706225.aspx)|  
|[Support for SQL Server AlwaysOn for highly available databases](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1511-for-System-Center-Configuration-Manager.md#BKMK_AlwasyOn)|[1511](https://technet.microsoft.com/library/mt706225.aspx)|  
|[Service a server cluster](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1511-for-System-Center-Configuration-Manager.md#BKMK_ClusterServerUpdates)|[1511](https://technet.microsoft.com/library/mt706225.aspx)|  
|[Device Health Attestation](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1512-for-System-Center-Configuration-Manager.md#bkmk_devicehealth)|[1512](https://technet.microsoft.com/library/mt706223.aspx)|  
|[In-console monitoring for terms and conditions](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1512-for-System-Center-Configuration-Manager.md#bkmk_viewterms)|[1512](https://technet.microsoft.com/library/mt706223.aspx)|  
|[Improvements to Endpoint Protection policy settings](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1512-for-System-Center-Configuration-Manager.md#bkmk_EPpolicy)|[1512](https://technet.microsoft.com/library/mt706223.aspx)|  
|[Improvements to Microsoft Intune integration](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1601-for-System-Center-Configuration-Manager.md#bkmk_hybrid1)|[1601](https://technet.microsoft.com/library/mt706226.aspx)|  
|[Client online status](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1601-for-System-Center-Configuration-Manager.md#bkmk_clientStatus)|[1601](https://technet.microsoft.com/library/mt706226.aspx)|  
|[Improvements to application management](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1601-for-System-Center-Configuration-Manager.md#bkmk_appmgmt1601)|[1601](https://technet.microsoft.com/library/mt706226.aspx)|  
|[Improvements to compliance settings](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1601-for-System-Center-Configuration-Manager.md#bkmk_compliance1601)|[1601](https://technet.microsoft.com/library/mt706226.aspx)|  
|[Improvements to mobile device management](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1602-for-System-Center-Configuration-Manager.md#BKMK_MDM)|[1602](https://technet.microsoft.com/library/mt706221.aspx)|  
|[Improvements to Software Center in the 1602 release](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1602-for-System-Center-Configuration-Manager.md#BKMK_SC1601)|[1602](https://technet.microsoft.com/library/mt706221.aspx)|  
|[Improvements to Windows 10 Servicing](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1602-for-System-Center-Configuration-Manager.md#BKMK_Win10Servicing)|[1602](https://technet.microsoft.com/library/mt706221.aspx)|  
|[Improvements to Software Center in the 1603 release](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1603-for-System-Center-Configuration-Manager.md#BKMK_SC1603)|[1603](https://technet.microsoft.com/library/mt706227.aspx)|  
|[Improvements to remote control](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1603-for-System-Center-Configuration-Manager.md#BKMK_RC1603)|[1603](https://technet.microsoft.com/library/mt706227.aspx)|  
|[Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1603-for-System-Center-Configuration-Manager.md#BKMK_RamDiskTFTP)|[1603](https://technet.microsoft.com/library/mt706227.aspx)|  
|[Manage volume-purchased apps from the Windows Store for Business](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1604-for-System-Center-Configuration-Manager.md#BKMK_WindowsVPP)|[1604](https://technet.microsoft.com/library/mt706224.aspx)|  
|[Improvements to Microsoft Passport for Work management](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1604-for-System-Center-Configuration-Manager.md#BKMK_PFW)|[1604](https://technet.microsoft.com/library/mt706224.aspx)|  
|[Option for clients to switch to a new software update point](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1604-for-System-Center-Configuration-Manager.md#bkmk_switchsup)|[1604](https://technet.microsoft.com/library/mt706224.aspx)|  
|[Client settings to manage Client Cache Settings and client Peer Cache](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1604-for-System-Center-Configuration-Manager.md#bkmk_peercache)|[1604](https://technet.microsoft.com/library/mt706224.aspx)|  
|[Support for Passport for Work as a KSP](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1604-for-System-Center-Configuration-Manager.md#bkmk_passport)|[1604](https://technet.microsoft.com/library/mt706224.aspx)|  
|[On-premises Device Health Attestation](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1604-for-System-Center-Configuration-Manager.md#bkmk_onpremdha)|[1604](https://technet.microsoft.com/library/mt706224.aspx)|  
|[SmartLock setting for Android devices](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1604-for-System-Center-Configuration-Manager.md#BKMK_Smart)|[1604](https://technet.microsoft.com/library/mt706224.aspx)|  
|[Per-app VPN for Windows 10 devices](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_PerAppVPN)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Improvements to the Install software updates task sequence](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_InstallSU)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Improvements to the Prepare ConfigMgr Client for Capture task sequence step](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_PrepareConfigMgrClient)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Grace period for required application deployments](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_Grace)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[New experience for remote device actions](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_Remote)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Windows Store for Business apps](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_WSFB)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[General improvements for volume-purchased apps](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_VPP2)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Enterprise Data Protection (EDP)](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_VPP)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[End users can install apps from the Company Portal](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_End)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[New tabs for Updates and Operating Systems in Software Center](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_SW1)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Service a server group](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_ServerGroups)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Support for Windows Defender Advanced Threat Protection service](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_ATP)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[New restart options for Windows 10 clients after software update installation](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_RestartOptions)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[On-premises Device Health Attestation](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_DHA)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Pre-declare corporate-owned devices with IMEI or iOS serial number](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1605-for-System-Center-Configuration-Manager.md#BKMK_IMEI)|[1605](https://technet.microsoft.com/library/mt706220.aspx)|  
|[Multiple device management points for On-premises Mobile Device Management](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#dmp_onprem)|[1606](https://technet.microsoft.com/library/mt732696.aspx)|
|[Automatically categorize devices into collections](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#dmp_category)|[1606](https://technet.microsoft.com/library/mt732696.aspx)|
|[Enforcement grace period for required application and software update deployments](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#dmp_grace)|[1606](https://technet.microsoft.com/library/mt732696.aspx)|
|[Using Configuration Manager as a Managed Installer with Device Guard](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#dmp_devg)|[1606](https://technet.microsoft.com/library/mt732696.aspx)|
|[Cloud Proxy Service](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#cloud_proxy) | [1606](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md) |  
|[Manage the Office 365 client agent in Configuration Manager](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#manage_o365) |[1606](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md) |
 |[The OSDPreserveDriveLetter task sequence variable has been deprecated](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#osdpreservedriveletter) |[1606](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md) |
[Changes for the Updates and Servicing Node](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md#updatesandservicing)|[1606](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1606-for-System-Center-Configuration-Manager.md) |
|[Improvements to the Windows 10 Edition Upgrade Policy](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1607-for-System-Center-Configuration-Manager.md#dmp_edition)|[1607](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1607-for-System-Center-Configuration-Manager.md)|
|[Customizable Branding for Software Center Dialogs](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1607-for-System-Center-Configuration-Manager.md#Customizable-Branding-for-Software-Center-Dialogs)|[1607](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1607-for-System-Center-Configuration-Manager.md)|  
|[Improvements to the Prepare ConfigMgr Client for Capture task sequence step](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md#Improvements-to-the-Prepare-ConfigMgr-Client-for-Capture-task-sequence-step)|[1608](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md)|
|[Improvements to Software Center](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md#Improvements-to-Software-Center)|[1608](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md)|
|[Improvements to Asset Intelligence](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md#Improvements-to-Asset-Intelligence)|[1608](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md)|
|[Remote control keyboard translation](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md#Remote-control-keyboard-translation)|[1608](../System Center Configuration Manager/Capabilities-in-Technical-Preview-1608-for-System-Center-Configuration-Manager.md)|
## See Also  
[What's new in System Center Configuration Manager](What%E2%80%99s%20new%20in%20System%20Center%20Configuration%20Manager%20incremental%20versions.md)
 [Introduction to System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-System-Center-Configuration-Manager.md)