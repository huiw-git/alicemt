---
title: "Prerequisites for software updates in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
caps.latest.revision: 18
caps.handback.revision: 0
---
# Prerequisites for software updates in System Center Configuration Manager
This topic lists the prerequisites for software updates in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. For each of these, the external dependencies and internal dependencies are listed in separate tables.  
  
## Software Update Dependencies External to Configuration Manager  
 The following sections  list the external dependencies for software updates.  
  
### Internet Information Services (IIS)  
 Internet Information Services (IIS) must be on site system servers in order to run the software update point, the management point, and the distribution point. For more information, see [Prerequisites for site system roles](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md#bkmk_Prrequisites).  
  
### Windows Server Update Services (WSUS)  
 WSUS is necessary for software updates synchronization and for the software updates compliance assessment scan on clients. The WSUS server must be installed before you create the software update point site system role. The following versions of WSUS are supported for a software update point:  
  
-   WSUS 4 (role in Windows Server 2012 and Windows Server 2012 R2)  
  
-   WSUS 3.2 (role in Windows Server 2008 R2)  
  
 When you have multiple software update points at a site, ensure that they are all running the same version of WSUS.  
  
> [!WARNING]  
>  The **Upgrades** software updates classification is only supported beginning in WSUS 4.0. Before you synchronize this new classification and have the ability to evaluate Windows 10 computers in a Windows 10 servicing plan, it is critical that you install [hotfix 3095113](https://support.microsoft.com/kb/3095113) for WSUS  on your software update points and site servers. This hotfix enables WSUS on a Windows Server 2012-based or a Windows Server 2012 R2-based server to sync and distribute feature upgrades for Windows 10. For more information, see [Manage Windows as a service using System Center Configuration Manager](../System Center Configuration Manager/Manage-Windows-as-a-service-using-System-Center-Configuration-Manager.md).  
>   
>  If you synchronize software updates with the **Upgrades** classification before you install [hotfix 3095113](https://support.microsoft.com/kb/3095113), see [Recover from synchronizing the Upgrades category before you install KB 3095113](#BKMK_RecoverUpgrades).  
  
### WSUS Administration Console  
 The WSUS Administration Console is required on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server when the software update point is on a remote site system server and WSUS is not already installed on the site server.  
  
> [!IMPORTANT]  
>  The WSUS version on the site server must be the same as the WSUS version running on the software update points.  
  
> [!IMPORTANT]  
>  Do not use the WSUS Administration Console to configure WSUS settings. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] connects to WSUS that is running on the software update point and configures the appropriate settings.  
  
### Windows Update Agent (WUA)  
 The WUA client is required on clients to enable them to connect to the WSUS server and retrieve the list of software updates that must be scanned for compliance.  
  
 When you install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], the latest version of the WUA is downloaded. Then, when the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is installed, the WUA is upgraded if necessary. However, if the installation fails, you must use a different method to upgrade the WUA.  
  
## Software Update Dependencies Internal to Configuration Manager  
 The following sections list the internal dependencies for software updates in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
### Management points  
 Management points transfer information between client computers and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. They are required for software updates.  
  
### Software update point  
 You must install a software update point on the WSUS server to be able to deploy software updates in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For more information, see [Configure software updates in System Center Configuration Manager](../System Center Configuration Manager/Configure-software-updates-in-System-Center-Configuration-Manager.md)  
  
### Distribution points  
 Distribution points are required to store the content for software updates. For more information about how to install distribution points and manage content, see [Manage content and content infrastructure for System Center Configuration Manager](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md).  
  
### Client settings for software updates  
 By default, software updates is enabled for clients. However there are other available settings that control how and when clients assess compliance for the software updates and control how the software updates are installed.  
  
 For more information, see the following:  
  
-   The Client Settings for Software Updates section in the [Configure software updates in System Center Configuration Manager](../System Center Configuration Manager/Configure-software-updates-in-System-Center-Configuration-Manager.md) topic.  
  
-   The  Software Updates section in the [About client settings in System Center Configuration Manager](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md) topic.  
  
### Reporting services point  
 The reporting services point site system role can display reports for software updates. This role is optional, but recommended. For more information about how to create a reporting services point, see [Configuring reporting in System Center Configuration Manager](../System Center Configuration Manager/Configuring-reporting-in-System-Center-Configuration-Manager.md) .  
  
##  <a name="BKMK_RecoverUpgrades"></a> Recover from synchronizing the Upgrades category before you install KB 3095113  
 You must install [hotfix 3095113](https://support.microsoft.com/kb/3095113) for WSUS  on your software update points and site servers before you synchronize the **Upgrades** classification. If the hotfix is not installed when the **Upgrades** classification is enabled, WSUS will see the Windows 10 build 1511 feature upgrade even if it can’t properly download and deploy the associated packages. If you synchronize any upgrades without having first installed [hotfix 3095113](https://support.microsoft.com/kb/3095113), you will populate the WSUS database (SUSDB) with unusable data that must be cleared before upgrades can be properly deployed.  Use the following procedure to recover from this issue.  
  
#### To recover from synchronizing the Upgrades classification before you install KB 3095113  
  
1.  Delete software updates with the Upgrades classification. You can use a PowerShell script similar to the following sample script:  
  
    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  
  
    > [!IMPORTANT]  
    >  You must run the script on all software update points in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy before you go to the next step.  
  
     To bulk delete software updates with the Upgrades classification, you can modify the PowerShell script to read multiple GUIDs from a txt file.  
  
2.  Uncheck the **Upgrades** classification in the [Software Update Point component properties](https://technet.microsoft.com/library/mt612804.aspx) and then start a [software updates synchronization](https://technet.microsoft.com/library/mt612804.aspx).  
  
3.  Install [hotfix 3095113](https://support.microsoft.com/kb/3095113) for WSUS  on your software update points and site servers.  
  
4.  Select the **Upgrades** classification in the [Software Update Point component properties](https://technet.microsoft.com/library/mt612804.aspx) and then start a [software updates synchronization](https://technet.microsoft.com/library/mt612804.aspx).  
  
## See Also  
 [Plan for software updates in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-software-updates-in-System-Center-Configuration-Manager.md)