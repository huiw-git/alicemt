---
title: "Prerequisites for remote control in System Center Configuration Manager"
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
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
caps.latest.revision: 6
caps.handback.revision: 0
author: barlanmsft
---
# Prerequisites for remote control in System Center Configuration Manager
Remote control in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] has external dependencies and dependencies in the product.  
  
## Dependencies external to Configuration Manager  
  
|Dependency|More information|  
|----------------|----------------------|  
|Computer video card driver|Ensure that the most up-to-date video driver is installed on client computers to ensure optimal remote control performance.|  
  
 Devices that run Windows Embedded, Windows Embedded for Point of Service (POS), and Windows Fundamentals for Legacy PCs do not support the remote control viewer, but they do support the remote control client.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] remote control cannot be used to remotely administer client computers that run Systems Management Server 2003 or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007.  
  
> [!NOTE]  
>  No Windows services are required as an external dependency for remote control.  
  
### Supported operating systems for the remote control viewer  
 The following table provides information about the supported operating systems for the remote control viewer. For information about supported client operating systems, see [Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md).  
  
|Operating system|Viewer support|More information|  
|----------------------|--------------------|----------------------|  
|Windows XP (32-bit)|Yes|To run the remote control viewer on this operating system, you must first download and install the [Remote Desktop Connection (RDC) client update 7.0 (KB969084)](http://go.microsoft.com/fwlink/?LinkId=232483) from the Microsoft Download Center.|  
|Windows XP (64-bit)|No|No additional information.|  
|Windows Vista (32-bit)|Yes|To run the remote control viewer on this operating system, you must first download and install the [Remote Desktop Connection (RDC) client update 7.0 (KB969084)](http://go.microsoft.com/fwlink/?LinkId=232483) from the Microsoft Download Center.|  
|Windows Vista (64-bit)|Yes|To run the remote control viewer on this operating system, you must first download and install the [Remote Desktop Connection (RDC) client update 7.0 (KB969084)](http://go.microsoft.com/fwlink/?LinkId=232483) from the Microsoft Download Center.|  
|Windows 7 (32-bit)|Yes|No additional information.|  
|Windows 7 (64-bit)|Yes|No additional information.|  
|Windows Server 2003 (32-bit)|No|No additional information.|  
|Windows Server 2003 (64-bit)|No|No additional information.|  
|Windows Server 2008 (32-bit)|No|No additional information.|  
|Windows Server 2008 (64-bit)|No|No additional information.|  
|Windows Server 2008 R2 (64-bit)|Yes|No additional information.|  
  
## Configuration Manager dependencies  
  
|Dependency|More information|  
|----------------|----------------------|  
|Remote control must be enabled for clients|By default, remote control is not enabled when you install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For information about how to enable and configure remote control, see [Configuring remote control in System Center Configuration Manager](../System Center Configuration Manager/Configuring-remote-control-in-System-Center-Configuration-Manager.md).|  
|Reporting services point|The reporting services point site system role must be installed before you can run reports for remote control. For more information, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).|  
|Security permissions to manage remote control|To access collection resources and to initiate a remote control session from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console: **Control AMT**, **Read**, **Read Resource**, and **Remote Control** permission for the **Collection** object.<br /><br /> The **Remote Tools Operator** security role includes these permissions that are required to manage remote control in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].<br /><br /> For more information, see [Configure role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Configure-role-based-administration-for-System-Center-Configuration-Manager.md).<br /><br /> Additionally, you must add users whom you want to give permission to use remote control and remote assistance to the remote control permitted views list by using the option **Permitted viewers of Remote Control and Remote Assistance** in the **Remote Tools** client settings.|  
  
## See Also  
 [Remote control technical reference for System Center Configuration Manager](../System Center Configuration Manager/Remote-control-technical-reference-for-System-Center-Configuration-Manager.md)