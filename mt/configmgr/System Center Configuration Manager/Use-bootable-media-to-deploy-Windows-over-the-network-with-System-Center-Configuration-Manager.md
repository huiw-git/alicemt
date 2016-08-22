---
title: "Use bootable media to deploy Windows over the network with System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: 5
---
# Use bootable media to deploy Windows over the network with System Center Configuration Manager
Bootable media deployments in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] let you deploy the operating system when the destination computer starts. When the destination computer starts, it retrieves the task sequence, the operating system image, and any other required content from the network. Because that content is not included on the media, you can update the content without having to re-create the media.  
  
 You can deploy operating systems over the network by using multicast in the following operating system deployment scenarios:  
  
-   [Refresh an existing computer with a new version of Windows using System Center Configuration Manager](../System Center Configuration Manager/Refresh-an-existing-computer-with-a-new-version-of-Windows-using-System-Center-Configuration-Manager.md)  
  
-   [Install a new version of Windows on a new computer (bare metal) with System Center Configuration Manager](../System Center Configuration Manager/Install-a-new-version-of-Windows-on-a-new-computer--bare-metal--with-System-Center-Configuration-Manager.md)  
  
-   [Replace an existing computer and transfer settings with System Center Configuration Manager](../System Center Configuration Manager/Replace-an-existing-computer-and-transfer-settings-with-System-Center-Configuration-Manager.md)  
  
 Complete the steps in one of the operating system deployment scenarios and then use the following sections to use bootable media to deploy the operating system.  
  
## Configure deployment settings  
 When you use bootable media to start the operating system deployment process, you must configure the deployment to make the operating system available to media. You can configure this on the **Deployment Settings** page of the Deploy Software Wizard or the **Deployment Settings** tab in the properties for the deployment.  For the **Make available to the following** setting, configure one of the following:  
  
-   **Configuration Manager clients, media and PXE**  
  
-   **Only media and PXE**  
  
-   **Only media and PXE (hidden)**  
  
## Create the bootable media  
 You can specify whether the  bootable media is a USB flash drive or CD/DVD set. The computer that will start the media must support the option that you choose as  a bootable drive. For more information, see [Create bootable media with System Center Configuration Manager](../System Center Configuration Manager/Create-bootable-media-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_Deploy"></a> Install the operating system from  bootable media  
 Insert the bootable media in a bootable drive on the computer, and then power it on to install the operating system.  
  
## See Also  
 [Methods to deploy enterprise operating systems using System Center Configuration Manager](../System Center Configuration Manager/Methods-to-deploy-enterprise-operating-systems-using-System-Center-Configuration-Manager.md)