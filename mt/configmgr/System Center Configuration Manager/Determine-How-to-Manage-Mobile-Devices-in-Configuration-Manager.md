---
title: "Determine How to Manage Mobile Devices in Configuration Manager"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c3041788-6717-493e-8d1a-402a6acc7d2e
caps.latest.revision: 5
---
# Determine How to Manage Mobile Devices in Configuration Manager
Use the information in this topic to help you decide how to manage mobile devices in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. There are different options for you to choose from depending on the mobile device platforms that you have in your environment and the management functionality that you need. The following options are available:  
  
-   [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] enrollment supports all major mobile device operating systems, including Windows Phone, Windows RT, iOS, and Android. It also provides is the most advanced management functionality, allows you to manage any mobile device from any location, and provides a single management console to manage mobile devices and on-premises computers.  
  
-   The Exchange Server connector enables [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to connect to multiple Exchange servers, centralizing management of devices that can connect to Exchange ActiveSync. You can configure Exchange mobile device management features, such as remote device wipe and settings control for multiple Exchange servers, from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] mobile device enrollment provides robust management including software deployment and configuration baselines for Windows Mobile and Nokia Symbian Belle operating systems.  
  
-   The mobile device legacy client provides software deployment, software inventory, and monitoring for Windows CE and Windows Mobile 6.0 operating systems.  
  
## General information to help you choose a mobile device management solution  
 Use the information in this section as general guidance to choose a mobile device management solution.  
  
### Enrollment by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)]  
 Manage mobile devices by integrating [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to enroll mobile devices when the following conditions apply:  
  
-   The mobile device platform is supported by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] mobile device enrollment.  
  
-   You want additional management features or settings that are not supported by the other mobile device management options.  
  
### Enrollment by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
 Use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to enroll mobile devices when the mobile operating system is supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] mobile device enrollment and when both of the following conditions apply:  
  
-   You have a Microsoft enterprise CA to issue and manage the required certificates.  
  
-   You want the additional management features or settings that are not supported by the Exchange Server connector, such as software installation and full hardware inventory.  
  
    > [!IMPORTANT]  
    >  If the mobile device synchronizes with Exchange Server, set the Exchange flag **AllowExternalDeviceManagement** to ensure that the mobile device continues to receive email from Exchange after it is enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. If you install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Exchange Server connector, you can set this flag by configuring the option **External mobile device management** in the Exchange Server connector properties. If you do not install the connector, you must set this flag by using the Exchange management tools. For example, use the PowerShell cmdlet Set-ActiveSyncMailPolicy with the parameter **AllowExternalDeviceManagement**.  
  
### Mobile device legacy client  
 Use the mobile device legacy client when the mobile operating system is not supported by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] mobile device enrollment and when both of the following conditions apply:  
  
-   You can install the required PKI certificates on the mobile device and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site systems (management point and distribution point).  
  
-   You want to install software packages on the mobile device and collect hardware inventory.  
  
### Exchange Server connector  
 Manage mobile devices by using the Exchange Server connector when the mobile device can connect to Exchange Server by using ActiveSync and when either of the following conditions applies:  
  
-   You do not require the security that a PKI offers or you do not have a PKI.  
  
-   You do not require all the management functions and settings that enrollment provides.  
  
## Choose a mobile device management solution based on supported mobile device platforms  
 You can enroll devices that run Windows Phone 8, Windows RT, and iOS by using the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] connector. You can also use the Exchange Server connector, use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to enroll mobile devices and install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, or use the mobile device legacy client (for example, for Windows CE mobile operating systems).  
  
 Use the following table to help you decide what mobile device management methods support the mobile device platforms you have in your environment.  
  
> [!NOTE]  
>  Not all mobile device platforms are listed in this table. For more information about the mobile operating systems that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports, see [Mobile Device Requirements](assetId:///c1e93ef9-761f-4f60-8372-df9bf5009be0#BKMK_SupConfigMobileClientReq).  
  
|Platform|Enrollment by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)]<sup>1</sup>|Enrollment by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]<sup>2</sup>|Mobile device legacy client<sup>3</sup>|Exchange Server connector<sup>4</sup>|  
|--------------|-------------------------------------------------------|-----------------------------------------------------|---------------------------------------------|-------------------------------------------|  
|iOS|Yes|||Yes|  
|Android|Yes|||Yes<sup>5</sup>|  
|Windows Phone 8.1|Yes|||Yes|  
|Windows Phone 8|Yes|||Yes|  
|Windows 8.1 RT|Yes|||Yes|  
|Windows 8 RT|Yes|||Yes|  
|Windows 8.1|Yes|||Yes|  
|Windows Phone 7||||Yes|  
|Nokia Symbian Belle||Yes||Yes|  
|Windows Mobile 6.5||Yes||Yes|  
|Windows Mobile 6.1||Yes||Yes|  
|Windows CE 5.0 (Arm and x86 processors)|||Yes|Yes|  
|Windows CE 6.0 (Arm and x86 processors)|||Yes|Yes|  
|Windows CE 7.0 (Arm and x86 processors)|||Yes|Yes|  
|Windows Mobile 6.0|||Yes|Yes|  
  
 <sup>1</sup> For details about what [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] versions support enrollment by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)], see [Mobile Devices Enrolled by Microsoft Intune](assetId:///c1e93ef9-761f-4f60-8372-df9bf5009be0#BKMK_MDMIntune).  
  
 <sup>2</sup> For details about what [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] versions support enrollment by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Mobile Devices Enrolled by Configuration Manager](assetId:///c1e93ef9-761f-4f60-8372-df9bf5009be0#BKMK_SupConfigMobileEnrolled).  
  
 <sup>3</sup> For details about what [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] versions support enrollment by using the mobile device legacy client, see [Mobile Device Legacy Client](assetId:///c1e93ef9-761f-4f60-8372-df9bf5009be0#BKMK_MDMLegacy).  
  
 <sup>4</sup> [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] offers limited management for mobile devices when you use the Exchange Server connector for Exchange Active Sync (EAS) capable devices that connect to a server running Exchange Server or Exchange Online. For details about what [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] versions support enrollment by using the Exchange Server Connector, see [Mobile Device Support by Using the Exchange Server Connector](assetId:///c1e93ef9-761f-4f60-8372-df9bf5009be0#BKMK_SupConfigMobileExchCon).  
  
 <sup>5</sup> Many mobile phones and tablets with the Android operating system support Exchange ActiveSync. However, these mobile devices may not support all available mobile device mailbox policies.  
  
## Choose a mobile device management solution based on management functionality  
 After you narrow down the mobile device management methods that you can use for the mobile device platforms you have in your environment, use the following table to decide what management method provides the management functionality that you need in your environment.  
  
|Management functionality|Enrollment by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)]|Enrollment by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]|Mobile device legacy client|Exchange Server connector|  
|------------------------------|-------------------------------------------|-----------------------------------------|---------------------------------|-------------------------------|  
|Public key infrastructure (PKI) security between the mobile device and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] by using mutual authentication and SSL to encrypt data transfers|Yes|Yes<br /><br /> More information: Requires Active Directory Certificate Services and an enterprise certification authority (CA). The mobile device certificates are installed automatically by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] during the enrollment process.|Yes<br /><br /> More information: Any PKI that meets the certificate requirements. The mobile device certificates must be installed independently from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].|No|  
|Client installation|No<br /><br /> More information: Instead of a client the user installs or connects to a company portal.|Yes<br /><br /> More information: Installed by the user from the browser on the mobile device.|Yes<br /><br /> More information: Installed by an administrative user by deploying a package and program.|No|  
|Support over the Internet|Yes|Yes|Yes|Yes|  
|Discovery|No|No|No|Yes|  
|Hardware inventory|Yes|Yes<br /><br /> More information: You can collect default information and create your own customized hardware inventory.|Yes|Yes<br /><br /> More information: Limited by what Exchange Server collects.|  
|Software inventory|No|No|Yes<br /><br /> More information: List of installed software only; you cannot inventory all files and you cannot collect files.|No|  
|Settings|Yes|Yes<br /><br /> More information: Deploy configuration baselines that contain mobile device configuration items. You can configure default settings and create your own customized settings.|No|Yes<br /><br /> More information: Limited by the settings in the default Exchange ActiveSync mailbox policies.|  
|Software deployment|Yes<br /><br /> More information: You can deploy available apps that users can download from the company portal.|Yes<br /><br /> More information: You can deploy required applications (install and uninstall), but not packages or software updates. Available applications, which users request from the Application Catalog, are not supported for mobile devices. Mobile devices also do not support simulated deployments.|Yes<br /><br /> More information: You can deploy packages, but not applications or software updates.|No|  
|Monitor with the fallback status point|No|No|Yes|No|  
|Connections to management points|No|Yes<br /><br /> More information: A single management point in the client’s assigned (primary) site.|Yes<br /><br /> More information: A single management point in primary sites and secondary sites.|No|  
|Connections to distribution points|Yes<br /><br /> More information: manage.microsoft.com is the only distribution point that is used.|Yes<br /><br /> More information: Distribution points in the assigned (primary) site.|Yes<br /><br /> More information: Distribution points in primary sites and secondary sites.|No|  
|Block from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]|Yes|Yes|Yes|No|  
|Quarantine and block from Exchange Server (and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)])|No|No|No|Yes|  
|Remote wipe|Yes|Yes<br /><br /> More information: By [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and by a user from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Application Catalog.|No|Yes<br /><br /> More information: By [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and by a user if supported by Exchange.|  
  
 For more information about the mobile operating systems that [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] supports, see [Supported Configurations for Configuration Manager 2012](assetId:///c1e93ef9-761f-4f60-8372-df9bf5009be0).  
  
## Dual Management: Enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and Managed by Using the Exchange Server Connector  
 You can enroll a mobile device by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and also manage it by using the Exchange Server connector. In this scenario, although you see only one mobile device in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you have dual management for a mobile device and the following consequences:  
  
-   No settings are applied from the Exchange Server connector; you must configure the mobile device settings by deploying a configuration baseline.  
  
-   If you collect hardware inventory by enabling the client setting for hardware inventory and by using the Exchange Server connector, the hardware inventory information from the mobile device is consolidated by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].