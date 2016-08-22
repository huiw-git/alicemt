---
title: "Working with remote connection profiles in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: eea36ac7-b261-45da-b448-0358c9e74386
caps.latest.revision: 7
---
# Working with remote connection profiles in System Center Configuration Manager
Use [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] remote connection profiles to allow your users to remotely connect to work computers when they are not connected to the domain or if their personal computers are connected over the Internet.  
  
 Users can connect to their work PC from the following device types:  
  
-   Computers that run Microsoft Windows  
  
-   Devices that run iOS  
  
-   Devices that run Android  
  
 Remote connection profiles let you deploy Remote Desktop Connection settings to users in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. Users can then use the company portal to access any of their primary work computers through Remote Desktop by using the Remote Desktop Connection settings provided by the company portal.  
  
 Microsoft Intune is required if you want users to connect to their work PCs by using the company portal. If you are not using Intune, users can still use the information from the remote connection profile to connect to their work PCs by using Remote Desktop over a VPN connection.  
  
> [!IMPORTANT]  
>  When you specify remote connection profile settings by using the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, the settings are stored in the local policy of the client computer. These settings might override Remote Desktop settings configured by another application. Additionally, if you use Windows Group Policy to configure Remote Desktop settings, the settings specified in the Group Policy will override those configured by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 When you install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], a new security group, **Remote PC Connect**, is created. This group is populated when you deploy a remote connection profile that includes the primary users of the computer to which you deploy the profile. Although a local administrator can add user names to this group, these users will be removed from the group when deployed remote connection profiles are next evaluated for compliance.  
  
 If you manually add a user to this group, the user can initiate remote connections, but the connection information will not be published in the company portal.  
  
 If you manually remove from the group a user that has been added by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will automatically remediate this change by adding the user back when the remote connection profile is next evaluated for compliance.  
  
> [!IMPORTANT]  
>  If the user device affinity relationship between a user and a device changes (for example, the computer a user connects to, stops being a primary device of the user, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] disables the remote connection profile and Windows Firewall settings to prevent connections to the computer.  
  
## Prerequisites  
  
### External dependencies  
  
|Dependency|More information|  
|----------------|----------------------|  
|Remote Desktop Gateway server.|If you want to enable users to connect on the Internet from outside the company domain, you must install and configure a Remote Desktop Gateway server.<br /><br /> If Remote Desktop or Terminal Services settings are managed by another application or Group Policy settings, remote connection profiles might not work correctly. When you deploy remote connection profiles from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, its settings are stored in the local policy of the client computer. These settings might override Remote Desktop settings that are configured by another application. Additionally, if you use Group Policy settings to configure Remote Desktop settings, the settings that are specified in the Group Policy settings override the settings that are configured by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].<br /><br /> For more information about how to install and configure a Remote Desktop Gateway server, see the Windows Server documentation.|  
|If client computers run a host-based firewall, it must enable the Mstsc.exe program.|When you configure a remote connection profile, you must enable the **Allow Windows Firewall exception for connections on Windows domains and on private networks** setting. When this setting is enabled, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically configures Windows Firewall to enable the Mstsc.exe program. However, if client computers run a different host-based firewall, you must manually configure this firewall dependency.<br /><br /> Group Policy settings to configure Windows Firewall can override the configuration that you set in Configuration Manager. If you use Group Policy to configure Windows Firewall, ensure that Group Policy settings do not block the Mstsc.exe program.|  
  
### Configuration Manager dependencies  
  
|Dependency|More information|  
|----------------|----------------------|  
|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] must be connected to Microsoft Intune (known as a hybrid configuration).|For more information about connecting [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to Microsoft Intune, see Manage Mobile Devices with Configuration Manager and Microsoft Intune.|  
|In order for a user to connect to a work computer on the company network, that computer must be a primary device of the user.|For more information about user device affinity, see [Link users and devices with user device affinity in System Center Configuration Manager](../System Center Configuration Manager/Link-users-and-devices-with-user-device-affinity-in-System-Center-Configuration-Manager.md).|  
|Specific security permissions must have been granted to manage remote connection profiles.|The **Compliance Settings Manager** security role includes the permissions required to manage remote connection profiles. For more information, see <br />[Configure role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Configure-role-based-administration-for-System-Center-Configuration-Manager.md).|  
  
## Security and privacy considerations for remote connection profiles  
  
### Security considerations  
  
|Security best practice|More information|  
|----------------------------|----------------------|  
|Manually specify user device affinity instead of allowing users to identify their primary device. In addition, do not enable usage-based configuration.|Because you must enable **Allow all primary users of the work computer to remotely connect** before you can deploy a remote connection profile, always manually specify user device affinity. Do not consider the information that is collected from users or from the device to be authoritative. If you deploy remote connection profiles and a trusted administrative user does not specify user device affinity, unauthorized users might receive elevated privileges and then be able to remotely connect to computers.<br /><br /> If you do enable usage-based configuration, this information is collected through state messages for which [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not provide security. To help mitigate this threat, use Server Message Block (SMB) signing or Internet Protocol security (IPsec) between client computers and the management point.|  
|Restrict local administrative rights on the site server computer.|A user who has local administrative rights on the site server can manually add members to the Remote PC Connect security group that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically creates and maintains. This might cause an elevation of privileges because members who are added to this group receive Remote Desktop permissions.|  
  
### Privacy considerations  
  
-   If a user initiates a connection to a work computer from the company portal, a file with a .rdp or .wsrdp extension is downloaded that contains the device name and the Remote Desktop Gateway Server name that is required to initiate the Remote Desktop session. The file extension depends on the operating system of the device. For example, the Windows 7 and Windows 8 operating systems use an .rdp file, and Windows 8.1 uses a .wsrdp file.  
  
-   The user can choose to open or save the .rdp file. If the user chooses to open the .rdp file, the file might be stored in the cache for the web browser, depending on the retention settings that are configured for the browser. If the user chooses to save the file, the file is not stored in the browser cache. The file is saved until the user manually deletes it.  
  
-   The .wsrdp file is downloaded and automatically saved locally. This file is overwritten the next time that the user runs a Remote Desktop session.  
  
-   Before you configure remote connection profiles, consider your privacy requirements.  
  
## Next steps  
 Next, you'll likely want to start to create and deploy remote connection profiles.  
  
 For help with all settings you can use, see [How to create remote connection profiles in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-remote-connection-profiles-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Ensure device compliance with System Center Configuration Manager](../System Center Configuration Manager/Ensure-device-compliance-with-System-Center-Configuration-Manager.md)