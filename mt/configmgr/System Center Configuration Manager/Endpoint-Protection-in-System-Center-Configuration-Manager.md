---
title: "Endpoint Protection in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-27
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 76c90f64-d729-456b-8304-01852cd66fb6
caps.latest.revision: 11
---
# Endpoint Protection in System Center Configuration Manager
Endpoint Protection in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] lets you to manage antimalware policies and Windows Firewall security for client computers in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy.  
  
> [!IMPORTANT]  
>  You must be licensed to use Endpoint Protection to manage clients in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy.  
  
 When you use Endpoint Protection with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you have the following benefits:  
  
-   Configure antimalware policies, Windows Firewall settings, and manage Windows Defender Advanced Threat Protection to selected groups of computers  
  
-   Use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] software updates to download the latest antimalware definition files to keep client computers up-to-date  
  
-   Send email notifications, use in-console monitoring, and view reports to keep administrative users informed when malware is detected on client computers  
  
Windows 10 computers don't require any additional client for endpoint protection management. On Windows 8.1 and earlier computers, Endpoint Protection installs its own client in addition to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client. Endpoint Protection can manage. The Endpoint Protection client has the following capabilities:  
  
-   Malware and spyware detection and remediation  
  
-   Rootkit detection and remediation  
  
-   Critical vulnerability assessment and automatic definition and engine updates  
  
-   Network vulnerability detection through Network Inspection System  
  
-   Integration with Microsoft Active Protection Services to report malware to Microsoft. When you join this service, the Endpoint Protection client or Windows Defender can download the latest definitions from the Malware Protection Center when unidentified malware is detected on a computer.  
  
> [!NOTE]  
>  The [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] client can be installed on a server that runs Hyper-V and on guest virtual machines with supported operating systems. To prevent excessive CPU usage, [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] actions have a built-in randomized delay so that protection services do not run simultaneously.  
  
 In addition, [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] lets you to manage Windows Firewall settings in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
 [Example scenario: Using System Center Endpoint Protection to protect computers from malware in System Center Configuration Manager](../Topic/Example%20scenario:%20Using%20System%20Center%20Endpoint%20Protection%20to%20protect%20computers%20from%20malware%20in%20System%20Center%20Configuration%20Manager.md) shows how you might configure and manage [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] and the Windows Firewall.  
  
## Managing Malware with Endpoint Protection  
 Endpoint Protection in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] allows you to create antimalware policies that contain settings for Endpoint Protection client configurations. You can then deploy these antimalware policies to client computers and monitor them in the **[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] Status** node in the **Monitoring** workspace, or by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
 Additional information:  
  
-   [How to create and deploy antimalware policies for Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-and-deploy-antimalware-policies-for-Endpoint-Protection-in-System-Center-Configuration-Manager.md) - Create, deploy, and monitor antimalware policies with a list of the settings that you can configure  
  
-   [How to monitor Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-Endpoint-Protection-in-System-Center-Configuration-Manager.md) - Monitoring activity reports, infected client computers, and more.  
  
-   [How to manage antimalware policies and firewall settings for Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-manage-antimalware-policies-and-firewall-settings-for-Endpoint-Protection-in-System-Center-Configuration-Manager.md) - Remediate malware found on client computers  
  
## Managing Windows Firewall with Endpoint Protection  
 Endpoint Protection in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides basic management of the Windows Firewall on client computers. For each network profile, you can configure the following settings:  
  
-   Enable or disable the Windows Firewall.  
  
-   Block incoming connections, including those in the list of allowed programs.  
  
-   Notify the user when Windows Firewall blocks a new program.  
  
> [!NOTE]  
>  Endpoint Protection supports managing the Windows Firewall only.  
  
 For more information about how to create and deploy Windows Firewall policies for Endpoint Protection, see [How to create and deploy Windows Firewall policies for Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-and-deploy-Windows-Firewall-policies-for-Endpoint-Protection-in-System-Center-Configuration-Manager.md).  
  
## Windows Defender Advanced Threat Protection

Starting with the 1606 release of Configuration Manager (current branch), Endpoint Protection can help manage and monitor Windows Defender Advanced Threat Protection (ATP). Windows Defender ATP is a new service that will help enterprises to detect, investigate, and respond to advanced attacks on their networks. See [Windows Defender Advanced Threat Protection](../System Center Configuration Manager/Windows-Defender-Advanced-Threat-Protection.md).

## Endpoint Protection Workflow  
 Use the following diagram to help you understand the workflow to implement [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy.  
  
 ![Endpoint Protection Workflow](../System Center Configuration Manager/medias/Endpoint-Protection-Workflow.gif "Endpoint)  
  
## Endpoint Protection Client for Mac Computers and Linux Servers  
 System Center 2012 includes an Endpoint Protection client for Linux and for Mac computers. These clients are not supplied with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]; instead, you must download the following products from the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  
  
-   System Center 2012 Endpoint Protection for the Mac  
  
-   System Center 2012 Endpoint Protection for Linux  
  
> [!IMPORTANT]  
>  You must be a Microsoft Volume License customer to download the Endpoint Protection installation files for Linux and the Mac.  
  
 These products cannot be managed from the Configuration Manager console. However, a System Center Operations Manager management pack is supplied with the installation files, which allows you to manage the client for Linux by using Operations Manager.  
  
 For more information about how to install and manage the Endpoint Protection clients for Linux and Mac computers, use the documentation that accompanies these products, which is located in the **Documentation** folder.