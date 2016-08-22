---
title: "Replace an existing computer and transfer settings with System Center Configuration Manager"
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
ms.assetid: d28f4363-9e8a-4c54-9cb7-0594fabfff26
caps.latest.revision: 6
---
# Replace an existing computer and transfer settings with System Center Configuration Manager
This topic provides the general steps in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to replace an existing computer with a new computer. For this scenario, you can choose from many different deployment methods, such as bootable media, multicast, or Software Center. You can also  choose to install a state migration point to store settings and then restore them to the new operating system after it is installed. If you are unsure that this is the right operating system deployment scenario for you, see [Scenarios to deploy enterprise operating systems with System Center Configuration Manager](../System Center Configuration Manager/Scenarios-to-deploy-enterprise-operating-systems-with-System-Center-Configuration-Manager.md).  
  
 Use the following sections to refresh an existing computer with a new version of Windows.  
  
##  <a name="BKMK_Plan"></a> Plan  
  
-   **Plan for and implement  infrastructure requirements**  
  
     There are several infrastructure requirements that must be in place before you can deploy operating systems, such as Windows ADK, User State Migration Tool (USMT), Windows Deployment Services (WDS), supported hard disk configurations, etc. For more information, see [Infrastructure requirements for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Infrastructure-requirements-for-operating-system-deployment-in-System-Center-Configuration-Manager.md)  
  
-   **Install a state migration point (required only if you transfer settings)**  
  
     When you are going to capture settings from the existing computer, and then restore the settings to the new operating system, you must install a state migration point. For more information, see [State migration point](../System Center Configuration Manager/Prepare-site-system-roles-for-operating-system-deployments-with-System-Center-Configuration-Manager.md#BKMK_StateMigrationPoints).  
  
##  <a name="BKMK_Configure"></a> Configure  
  
1.  **Prepare a boot image**  
  
     Boot images start a computer in a Windows PE environment (a minimal operating system with limited components and services) that can then install a full Windows operating system on the computer.   When you deploy operating systems, you must select a boot image to use and distribute the image to a distribution point. Use the following to prepare the boot image:  
  
    -   To learn more about boot images, see [Manage boot images with System Center Configuration Manager](../System Center Configuration Manager/Manage-boot-images-with-System-Center-Configuration-Manager.md).  
  
    -   For more information about how  to customize a boot image, see [Customize boot images with System Center Configuration Manager](../System Center Configuration Manager/Customize-boot-images-with-System-Center-Configuration-Manager.md).  
  
    -   Distribute the boot image to distribution points. For more information, see [Distribute content](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_dist).  
  
2.  **Prepare an operating system image**  
  
     The operating system image contains the files necessary to install the operating system on the destination computer. Use the following to prepare the operating system image:  
  
    -   To learn more about how to create an operating system image, see  [Manage operating system images with System Center Configuration Manager](../System Center Configuration Manager/Manage-operating-system-images-with-System-Center-Configuration-Manager.md).  
  
    -   Distribute the operating system image to distribution points. For more information, see [Distribute content](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_dist).  
  
3.  **Create a task sequence to deploy operating systems over the network**  
  
     Use a task sequence to automate the installation of the operating system over the network. Use the steps in [Create a task sequence to install an operating system in System Center Configuration Manager](../System Center Configuration Manager/Create-a-task-sequence-to-install-an-operating-system-in-System-Center-Configuration-Manager.md) to create the task sequence to deploy the operating system. Depending on the deployment method that you choose, there might be additional considerations for the task sequence.  
  
    > [!NOTE]  
    >  In this scenario, if you capture and restore user settings and files, you can choose to use a state migration point or save the files locally. For more information, see [Manage user state in System Center Configuration Manager](../System Center Configuration Manager/Manage-user-state-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_Deploy"></a> Deploy  
  
-   Use one of the following deployment methods to deploy the operating system:  
  
    -   [Use Software Center to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-Software-Center-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md)  
  
    -   [Use bootable media to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-bootable-media-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md)  
  
    -   [Use multicast to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-multicast-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md)  
  
    -   [Create an image for an OEM in factory or a local depot with System Center Configuration Manager](../System Center Configuration Manager/Create-an-image-for-an-OEM-in-factory-or-a-local-depot-with-System-Center-Configuration-Manager.md)  
  
## Monitor  
  
-   **Monitor the task sequence deployment**  
  
     To monitor the task sequence deployment  to install the operating system, see [Monitor operating system deployments in System Center Configuration Manager](../System Center Configuration Manager/Monitor-operating-system-deployments-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Scenarios to deploy enterprise operating systems with System Center Configuration Manager](../System Center Configuration Manager/Scenarios-to-deploy-enterprise-operating-systems-with-System-Center-Configuration-Manager.md)