---
title: "Infrastructure requirements for operating system deployment in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
caps.latest.revision: 24
---
# Infrastructure requirements for operating system deployment in System Center Configuration Manager
Operating system deployment in [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] has external dependencies and dependencies within the product. Use the following sections to help you prepare for operating system deployment.  
  
-   [Dependencies External to Configuration Manager](#BKMK_ExternalDependencies)  
  
-   [Configuration Manager Dependencies](#BKMK_InternalDependencies)  
  
-   [Windows Deployment Services](#BKMK_WDS)  
  
-   [Supported Operating Systems](#BKMK_SupportedOS)  
  
-   [Supported Disk Configurations](#BKMK_SupportedDiskConfig)  
  
##  <a name="BKMK_ExternalDependencies"></a> Dependencies External to Configuration Manager  
 The following provides information about external tools, installation kits, and operating systems that are required to deploy operating systems in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
### Windows ADK for Windows 10  
 Windows ADK is a set of tools and documentation that support the configuration and deployment of Windows operating systems. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses Windows ADK to automate Windows installations, capture Windows images, migrate user profiles and data, and so on.  
  
 The following features of the Windows ADK must be installed on site server of the top-level site of the hierarchy, on the site server of each primary site in the hierarchy, and on the SMS Provider site system server:  
  
-   User State Migration Tool (USMT) <sup>1</sup>  
  
-   Windows Deployment Tools  
  
-   Windows Preinstallation Environment (Windows PE)  
  
 <sup>1</sup> USMT is not required on the SMS Provider site system server.  
  
> [!NOTE]  
>  You must manually install the Windows ADK on each computer that will host a central administration site or primary site server before you install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
 For more information, see:  
  
-   [Windows ADK for Windows 10 scenarios for IT Pros](https://technet.microsoft.com/library/mt280162\(v=vs.85\).aspx)  
  
-   [Download the Windows ADK for Windows 10](https://msdn.microsoft.com/windows/hardware/dn913721.aspx#adkwin10)  
  
### User State Migration Tool (USMT)  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses a USMT package that contains the USMT 10 source files to capture and restore the user state as part of your operating system deployment. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup at the top-level site automatically creates the USMT package. USMT 10 can capture user state from Windows 7, Windows 8, Windows 8.1, and Windows 10. USMT 10 is distributed in the Windows Assessment and Deployment Kit (Windows ADK) for Windows 10.  
  
 For more information, see:  
  
-   [Common Migration Scenarios for USMT 10](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)  
  
-   [Manage user state in System Center Configuration Manager](../System Center Configuration Manager/Manage-user-state-in-System-Center-Configuration-Manager.md)  
  
### Windows PE  
 Windows PE is used for boot images to start a computer. It is a Windows operating system with limited services that is used during the pre-installation and deployment of Windows operating systems. The following provides the version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and the supported version of Windows ADK, the Windows PE version on which the boot image is based that can be customized from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and the Windows PE versions on which the boot image is based that you can customize by using DISM and then add the image to the specified version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
#### Configuration Manager version 1511  
 The following provides the supported version of Windows ADK, the Windows PE version on which the boot image is based that can be customized from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and the Windows PE versions on which the boot image is based that you can customize by using DISM and then add the image to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   **Windows ADK version**  
  
     Windows ADK for Windows 10  
  
-   **Windows PE versions for boot images customizable from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console**  
  
     Windows PE 10  
  
-   **Supported Windows PE versions for boot images not customizable from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console**  
  
     Windows PE 3.1<sup>1</sup> and Windows PE 5  
  
     <sup>1</sup> You can only add a boot image to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] when it is based on Windows PE 3.1. Install the Windows AIK Supplement for Windows 7 SP1 to upgrade Windows AIK for Windows 7 (based on Windows PE 3) with the Windows AIK Supplement for Windows 7 SP1 (based on Windows PE 3.1). You can download Windows AIK Supplement for Windows 7 SP1 from the [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=5188).  
  
     For example, when you have [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can customize boot images from Windows ADK for Windows 10 (based on Windows PE 10) from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. However, while boot images based on Windows PE 5 are supported, you must customize them from a different computer and use the version of DISM that is installed with Windows ADK for Windows 8. Then, you can add the boot image to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. For more information with the steps to customize a boot image (add optional components and drivers), enable command support to the boot image, add the boot image to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and update distribution points with the boot image, see [Customize boot images with System Center Configuration Manager](../System Center Configuration Manager/Customize-boot-images-with-System-Center-Configuration-Manager.md). For more information about boot images, see [Manage boot images with System Center Configuration Manager](../System Center Configuration Manager/Manage-boot-images-with-System-Center-Configuration-Manager.md).  
  
### Windows Server Update Services (WSUS)  
You must install the following WSUS 4.0 hotfixes:
  - [Hotfix 3095113](https://support.microsoft.com/kb/3095113) is necessary for Windows 10 servicing, which uses the software updates infrastructure to get Windows 10 feature upgrades. When you have WSUS 3.2, you must use task sequences to upgrade Windows 10. For more information, see [Manage Windows as a service using System Center Configuration Manager](../System Center Configuration Manager/Manage-Windows-as-a-service-using-System-Center-Configuration-Manager.md).  
  - [Hotfix 3159706](https://support.microsoft.com/kb/3159706) is necessary to use Windows 10 servicing to upgrade computers to the Windows 10 Anniversary Update, as well as for subsequence versions. There are manual steps described in the support article that you must take to install this hotfix. For more information, see [Manage Windows as a service using System Center Configuration Manager](../System Center Configuration Manager/Manage-Windows-as-a-service-using-System-Center-Configuration-Manager.md).
  
  
### Internet Information Services (IIS) on the site system servers  
 IIS is required for  the distribution point, state migration point, and management point. For more information about this requirement, see [Site and site system prerequisites for System Center Configuration Manager](../System Center Configuration Manager/Site-and-site-system-prerequisites-for-System-Center-Configuration-Manager.md).  
  
### Windows Deployment Services (WDS)  
 WDS is needed for PXE deployments, when you use multicast to optimize bandwidth in your deployments, and for offline servicing of images. If the provider is installed on a remote server, you must install WDS on the site server and the remote provider. For more information, see [Windows Deployment Services](#BKMK_WDS) in this topic.  
  
### Dynamic Host Configuration Protocol (DHCP)  
 DHCP is required for PXE deployments. You must have a functioning DHCP server with an active host to deploy operating systems by using PXE. For more information about PXE deployments, see [Use PXE to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-PXE-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md).  
  
### Supported operating systems and hard disk configurations  
 For more information about the operating system versions and hard disk configurations that are supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] when you deploy operating systems, see [Supported Operating Systems](#BKMK_SupportedOS) and [Supported Disk Configurations](#BKMK_SupportedDiskConfig).  
  
### Windows device drivers  
 Windows device drivers can be used when you install the operating system on the destination computer and when you run Windows PE by using a boot image. For more information about device drivers, see [Manage drivers in System Center Configuration Manager](../System Center Configuration Manager/Manage-drivers-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_InternalDependencies"></a> Configuration Manager Dependencies  
 The following provides information about [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operating system deployment prerequisites.  
  
### Operating system image  
 Operating system images in Configuration Manager are stored in the Windows Imaging (WIM) file format and represent a compressed collection of reference files and folders that are required to successfully install and configure an operating system on a computer. For more information, see [Manage operating system images with System Center Configuration Manager](../System Center Configuration Manager/Manage-operating-system-images-with-System-Center-Configuration-Manager.md).  
  
### Driver catalog  
 To deploy a device driver, you must import the device driver, enable it, and make it available on a distribution point that the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client can access. For more information about the driver catalog, see [Manage drivers in System Center Configuration Manager](../System Center Configuration Manager/Manage-drivers-in-System-Center-Configuration-Manager.md).  
  
### Management point  
 Management points transfer information between client computers and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. The client uses a management point to run any task sequences that are required to complete the operating system deployment.  
  
 For more information about task sequences, see [Planning considerations for automating tasks in System Center Configuration Manager](../System Center Configuration Manager/Planning-considerations-for-automating-tasks-in-System-Center-Configuration-Manager.md).  
  
### Distribution point  
 Distribution points are used in most deployments to store the data that is used to deploy an operating system, such as the operating system image or device driver packages. Task sequences typically retrieve data from a distribution point to deploy the operating system.  
  
 For more information about how to install distribution points and manage content, see [Manage content and content infrastructure for System Center Configuration Manager](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md).  
  
### PXE-enabled distribution point  
 To deploy PXE-initiated deployments, you must configure a distribution point to accept PXE requests from clients. For more information about how to configure the distribution point, see [Distribution point configurations](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_DBtable) and find the PXE configuration category in the table.  
  
### Multicast-enabled distribution point  
 To optimize your operating system deployments by using multicast, you must configure a distribution point to support multicast. For more information about how to configure the distribution point, see [Distribution point configurations](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_DBtable) and find the Multicast configuration category in the table.  
  
### State migration point  
 When you capture and restore user state data for side-by-side and refresh deployments, you must configure a state migration point to store the user state data on another computer.  
  
 For more about how to configure the state migration point, see [State migration point](../System Center Configuration Manager/Prepare-site-system-roles-for-operating-system-deployments-with-System-Center-Configuration-Manager.md#BKMK_StateMigrationPoints).  
  
 For information about how to capture and restore user state, see [Manage user state in System Center Configuration Manager](../System Center Configuration Manager/Manage-user-state-in-System-Center-Configuration-Manager.md).  
  
### Service connection point  
 When you use Windows as a Service (WaaS) to deploy Windows 10 Current Branch, you must have the  service connection point installed. For more information, see [Manage Windows as a service using System Center Configuration Manager](../System Center Configuration Manager/Manage-Windows-as-a-service-using-System-Center-Configuration-Manager.md).  
  
### Reporting services point  
 To use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports for operating system deployments, you must install and configure a reporting services point. For more information, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
### Security permissions for operating system deployments  
 The **Operating System Deployment Manager** security role is a built-in role that cannot be changed. However, you can copy the role, make changes, and then save these changes as a new custom security role. Here are some of the permissions that apply directly to operating system deployments:  
  
-   **Boot Image Package**: Create, Delete, Modify, Modify Folder, Move Object, Read, Set Security Scope  
  
-   **Device Drivers**: Create, Delete, Modify, Modify Folder, Modify Report, Move Object, Read, Run Report  
  
-   **Driver Package**: Create, Delete, Modify, Modify Folder, Move Object, Read, Set Security Scope  
  
-   **Operating System Image**: Create, Delete, Modify, Modify Folder, Move Object, Read, Set Security Scope  
  
-   **Operating System Installation Package**: Create, Delete, Modify, Modify Folder, Move Object, Read, Set Security Scope  
  
-   **Task Sequence Package**: Create, Create Task Sequence Media, Delete, Modify, Modify Folder, Modify Report, Move Object, Read, Run Report, Set Security Scope  
  
 For more information about custom security roles, see [Create custom security roles](../System Center Configuration Manager/Configure-role-based-administration-for-System-Center-Configuration-Manager.md#BKMK_CreateSecRole).  
  
### Security scopes for operating system deployments  
 Use security scopes to provide administrative users with access to the securable objects used in operating system deployments, such as operating system and boot images, driver packages, and task sequence packages. For more information, see [Security scopes](../System Center Configuration Manager/Fundamentals-of-role-based-administration-for-System-Center-Configuration-Manager.md#bkmk_PlanScope).  
  
##  <a name="BKMK_WDS"></a> Windows Deployment Services  
 Windows Deployment Services (WDS) must be installed on the same server as the distribution points that you configure to support PXE or multicast. WDS is included in the operating system of the server. For PXE deployments, WDS is the service that performs the PXE boot. When the distribution point is installed and enabled for PXE, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs a provider into WDS that uses the WDS PXE boot functions.  
  
> [!NOTE]  
>  The installation of WDS might fail if the server requires a restart.  
  
 Other WDS configurations that must be considered include the following:  
  
-   The WDS installation on the server requires that the administrator is a member of the Local Administrators group.  
  
-   The WDS server must be either a member of an Active Directory domain or a domain controller for an Active Directory domain. All Windows domain and forest configurations support WDS.  
  
-   If the provider is installed on a remote server, you must install WDS on the site server and the remote provider.  
  
###  <a name="BKMK_WDSandDHCP"></a> Considerations when you have WDS and DHCP on the same server  
 Consider the following configuration issues if you plan to co-host the distribution point on a server running DHCP.  
  
-   You must have a functioning DHCP server with an active scope. Windows Deployment Services uses PXE, which requires a DHCP server.  
  
-   DHCP and Windows Deployment Services both require port number 67. If you co-host Windows Deployment Services and DHCP, you can move DHCP or the distribution point that is configured for PXE to a separate server. Or, you can use the following procedure to configure the Windows Deployment Services server to listen on a different port.  
  
    ##### To configure the Windows Deployment Services server to listen on a different port  
  
    1.  Modify the following registry key:  
  
         **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE**  
  
    2.  Set the registry value to: **UseDHCPPorts = 0**  
  
    3.  For the new configuration to take effect, run the following command on the server:  
  
         `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  
  
-   A DNS server is required to run Windows Deployment Services.  
  
-   The following UDP ports must be open on the Windows Deployment Services server.  
  
    -   Port 67 (DHCP)  
  
    -   Port 69 (TFTP)  
  
    -   Port 4011 (PXE)  
  
    > [!NOTE]  
    >  In addition, if DHCP authorization is required on the server, you need DHCP client port 68 to be open on the server.  
  
##  <a name="BKMK_SupportedOS"></a> Supported Operating Systems  
 All Windows operating systems listed as supported client operating systems in [Supported operating systems for clients and devices for System Center Configuration Manager](../System Center Configuration Manager/Supported-operating-systems-for-clients-and-devices-for-System-Center-Configuration-Manager.md) are supported for operating system deployments.  

##  <a name="BKMK_SupportedDiskConfig"></a> Supported Disk Configurations  
 The hard disk configuration combinations on the reference and destination computers that are supported for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operating system deployment are shown in the following table.  
  
|Reference computer hard disk configuration|Destination computer hard disk configuration|  
|------------------------------------------------|--------------------------------------------------|  
|Basic disk|Basic disk|  
|Simple volume on a dynamic disk|Simple volume on a dynamic disk|  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports capturing an operating system image only from computers that are configured with simple volumes. There is no support for the following hard disk configurations:  
  
-   Spanned volumes  
  
-   Striped volumes (RAID 0)  
  
-   Mirrored volumes (RAID 1)  
  
-   Parity volumes (RAID 5)  
  
 The following table shows an additional hard disk configuration on the reference and destination computers that is not supported with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operating system deployment.  
  
|Reference computer hard disk Configuration|Destination computer hard disk configuration|  
|------------------------------------------------|--------------------------------------------------|  
|Basic disk|Dynamic disk|  
  
## See Also  
 [Plan for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-operating-system-deployment-in-System-Center-Configuration-Manager.md)