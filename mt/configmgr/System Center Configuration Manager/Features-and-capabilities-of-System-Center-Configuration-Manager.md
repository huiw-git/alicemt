---
title: "Features and capabilities of System Center Configuration Manager"
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
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
caps.latest.revision: 18
caps.handback.revision: 0
---
# Features and capabilities of System Center Configuration Manager
The following   are the primary management capabilities of   
            [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].   
         Each capability has its own prerequisites, and the capabilities that you want to use might influence the design and implementation of your   
                    [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. For example, if you want to deploy software to devices in your hierarchy, you must install the distribution point site system role.  
  
 For more information about how to plan and install   
            [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to support these management capabilities in your environment, see   
            [Get ready for System Center Configuration Manager](../System Center Configuration Manager/Get-ready-for-System-Center-Configuration-Manager.md).  
  
 **Application management**  
  
 Provides a set of tools and resources that can help you create, manage, deploy, and monitor applications to a range of different devices that you manage. Additionally, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides you with tools that help you protect your company data in apps in user's apps. See  
                            [Deploy and manage applications with System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-applications-with-System-Center-Configuration-Manager.md)  
  
 **Company resource access**  
  
 Provides a set of tools and resources that enable you to give users in your organization access to data and applications from remote locations. These tools include Wi-Fi- profiles, VPN profiles, Certificate profiles, and conditional access to Exchange and SharePoint online. See  
                        [Protect data and site infrastructure with System Center Configuration Manager](../System Center Configuration Manager/Protect-data-and-site-infrastructure-with-System-Center-Configuration-Manager.md) and [Manage access to services in System Center Configuration Manager](../System Center Configuration Manager/Manage-access-to-services-in-System-Center-Configuration-Manager.md)  
  
 **Compliance settings**  
  
 Provides a set of tools and resources that can help you to assess, track, and remediate the configuration compliance of client devices in the enterprise.  Additionally, you can use compliance settings to configure a range of features and security settings on devices you manage. See  
                            [Ensure device compliance with System Center Configuration Manager](../System Center Configuration Manager/Ensure-device-compliance-with-System-Center-Configuration-Manager.md)  
  
 **Endpoint Protection**  
  
 Provides security, antimalware, and Windows Firewall management for computers in your enterprise. See   
                            [Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Endpoint-Protection-in-System-Center-Configuration-Manager.md)  
  
 **Inventory**  
  
 Provides a set of tools to help identify and monitor assets:  
  
-   **Hardware inventory**: Collects detailed information about the hardware of devices in your enterprise.  
                                     See  
                                        [Introduction to hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-hardware-inventory-in-System-Center-Configuration-Manager.md)  
  
-   **Software inventory**: Collects and reports information about the files that are stored on client computers in your organization.  
                                     See  
                                        [Introduction to software inventory in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-software-inventory-in-System-Center-Configuration-Manager.md)  
  
-   **Asset Intelligence**: Provides tools to collect inventory data and to monitor software license usage in your enterprise.  
                                    See   
                                        [Introduction to Asset Intelligence in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-Asset-Intelligence-in-System-Center-Configuration-Manager.md)  
  
 **Mobile device management with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)]**  
  
 You can use   
                            [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to manage iOS, Android (including Samsung KNOX), Windows Phone and Windows devices using the   
                            [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] service over the Internet.   
                        Although you use the   
                            [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] service, management tasks are completed by using the service connection point site system role available through the   
                            [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
                        See   
                                    [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md)  
  
 **On-premises Mobile Device Management**  
  
 Enrolls and manages PCs and mobile devices using the on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure and management functionality built into the device platforms (instead of relying on a separately installed [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client). Currently supports managing Windows 10 Enterprise and Windows 10 Mobile devices.  See [Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Manage-mobile-devices-with-on-premises-infrastructure-in-System-Center-Configuration-Manager.md)  
  
 **Operating system deployment**  
  
 Provides a tool to create operating system images. You can then use these images to deploy them to computers that are managed by   
                            [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and to unmanaged computers, by using PXE boot or bootable media such as a CD set, DVD, or USB flash drives.  
                             See [Introduction to operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-operating-system-deployment-in-System-Center-Configuration-Manager.md)  
  
 **Power management**  
  
 Provides a set of tools and resources that you can use to manage and monitor the power consumption of client computers in the enterprise. See   
                            [Introduction to power management in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-power-management-in-System-Center-Configuration-Manager.md)  
  
 **Queries**  
  
 Provides a tool to retrieve information about resources in your hierarchy and information about inventory data and status messages. You can then use this information for reporting or for defining collections of devices or users for software deployment and configuration settings. See  
                            [Introduction to queries in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-queries-in-System-Center-Configuration-Manager.md)  
  
 **Remote connection profiles**  
  
 Provides a set of tools and resources to help you to create, deploy and monitor remote connection settings to devices in your organization. By deploying these settings, you minimize the end-user effort required to connect to their computer on the corporate network. See  
                            [Working with remote connection profiles in System Center Configuration Manager](../System Center Configuration Manager/Working-with-remote-connection-profiles-in-System-Center-Configuration-Manager.md)  
  
 **User data and profiles configuration items**  
  
 User data and profiles configuration items in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] contain settings that can manage folder redirection, offline files and roaming profiles on computers that run Windows 8 and later for users in your hierarchy. See [Working with user data and profiles configuration items in System Center Configuration Manager](../System Center Configuration Manager/Working-with-user-data-and-profiles-configuration-items-in-System-Center-Configuration-Manager.md)  
  
 **Remote control**  
  
 Provides tools to remotely administer client computers from the   
                            [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
                         See   
                            [Introduction to remote control in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-remote-control-in-System-Center-Configuration-Manager.md)  
  
 **Reporting**  
  
 Provides a set of tools and resources that help you use the advanced reporting capabilities of SQL Server Reporting Services from the   
                            [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
                        See   
                            [Introduction to reporting in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-reporting-in-System-Center-Configuration-Manager.md)  
  
 **Software metering**  
  
 Provides tools to monitor and collect software usage data from   
                            [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients.  
                         See   
                            [Monitor app usage with software metering in System Center Configuration Manager](../System Center Configuration Manager/Monitor-app-usage-with-software-metering-in-System-Center-Configuration-Manager.md)  
  
 **Software updates**  
  
 Provides a set of tools and resources that can help you manage, deploy, and monitor software updates in the enterprise. See  
                            [Introduction to software updates in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-software-updates-in-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Introduction to System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-System-Center-Configuration-Manager.md)