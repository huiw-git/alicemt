---
title: "Support for Virtualization Environments for System Center Configuration Manager"
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
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
caps.latest.revision: 6
---
# Support for Virtualization Environments for System Center Configuration Manager
[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports installing the client and site system roles on supported operating systems that run as a virtual machine in the following virtualization environments. This support exists even when the virtual machine host (virtualization environment) is not supported as a client or site server.  
  
 **For example**, if you use Microsoft Hyper-V Server 2012 to host a virtual machine that runs Windows Server 2012, you can install the client or site system roles on the virtual machine (Windows Server 2012), but not on the host, (Microsoft Hyper-V Server 2012).  
  
|Virtualization environment|  
|--------------------------------|  
|Windows Server 2008 R2|  
|Microsoft Hyper-V Server 2008 R2|  
|Windows Server 2012|  
|Microsoft Hyper-V Server 2012|  
|Windows Server 2012 R2|  
  
 Each virtual computer that you use must meet or exceed the same hardware and software configuration that you would use for a physical [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] computer.  
  
 You can validate that your virtualization environment is supported for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] by using the Server Virtualization Validation Program and its online Virtualization Program Support Policy Wizard. For more information about the Server Virtualization Validation Program, see [Windows Server Virtualization Validation Program](http://go.microsoft.com/fwlink/p/?LinkId=134672).  
  
> [!NOTE]  
>  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support Virtual PC or Virtual Server guest operating systems that run on a Mac.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot manage virtual machines unless they are online. An offline virtual machine image cannot be updated nor can inventory be collected by using the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on the host computer.  
  
 No special consideration is given to virtual machines. For example, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] might not determine whether an update has to be re-applied to a virtual machine image if the virtual machine is stopped and restarted without saving the state of the virtual machine to which the update was applied.  
  
##  <a name="bkmk_Azure"></a> Microsoft Azure virtual machines  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is supported to run in virtual machines in Microsoft Azure just as it does when run on-premises within your physical corporate network. You can use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with Microsoft Azure virtual machines in the following scenarios:  
  
-   **Scenario 1:** You can run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in a Microsoft Azure virtual machine and use it to manage clients installed in other Microsoft Azure virtual machines.  
  
-   **Scenario 2:** You can run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in a Microsoft Azure virtual machine and use it to manage clients that are not running in Microsoft Azure.  
  
-   **Scenario 3:** You can run different [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system roles in Microsoft Azure virtual machines while running other roles in your physical corporate network (with appropriate network connectivity for communications).  
  
 The same [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] requirements for networks, supported configurations and hardware requirements that apply to installing [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] on-premises in your physical corporate network also apply to installation in Microsoft Azure.  
  
> [!IMPORTANT]  
>  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites and clients that run in Azure virtual machines are subject to the same license requirements as on-premises installations.  
  
## See Also  
 [Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md)