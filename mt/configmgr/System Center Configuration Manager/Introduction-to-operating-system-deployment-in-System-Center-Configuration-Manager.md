---
title: "Introduction to operating system deployment in System Center Configuration Manager"
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
ms.assetid: d9a1c545-8301-492c-832f-2c108ff93c77
caps.latest.revision: 12
---
# Introduction to operating system deployment in System Center Configuration Manager
The following sections explain some of the concepts that are used to deploy operating systems in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] environment:  
  
-   [The operating system deployment process](#BKMK_OSDeploymentProcess)  
  
-   [Operating system deployment scenarios](#BKMK_OSDScenarios)  
  
-   [Methods to deploy operating systems](#BKMK_OSDMethods)  
  
-   [Boot images](#BKMK_BootImages)  
  
-   [Operating system images](#BKMK_OSImages)  
  
-   [Operating system upgrade packages](#BKMK_OSUpgradePackages)  
  
-   [Media to deploy operating systems](#BKMK_OSDMedia)  
  
-   [Device drivers](#BKMK_DeviceDrivers)  
  
-   [Save and restore user state](#BKMK_OSDUserState)  
  
-   [Deploy to unknown computers](#BKMK_UnknownComputer)  
  
-   [Associate users with a computer](#BKMK_UDA)  
  
-   [Use task sequences to automate steps](#BKMK_TaskSequences)  
  
##  <a name="BKMK_OSDeploymentProcess"></a> The operating system deployment process  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides several methods that you can use to deploy an operating system. There are several actions that you must take regardless of the deployment method that you use:  
  
-   Identify Windows device drivers that are required to start the boot image or install the operating system image that you have to deploy.  
  
-   Identify the boot image that you want to use to start the destination computer.  
  
-   Use a task sequence to capture an image of the operating system that you will deploy. Alternatively, you can use a default operating system image.  
  
-   Distribute the boot image, operating system image, and any related content to a distribution point.  
  
-   Create a task sequence with the steps to deploy the boot image and the operating system image.  
  
-   Deploy the task sequence to a collection of computers.  
  
-   Monitor the deployment.  
  
##  <a name="BKMK_OSDScenarios"></a> Operating system deployment scenarios  
 There are many operating system deployment scenarios in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] that you can choose from depending on your environment and the purpose for the operating system installation.  For example, you can partition and format an existing computer with a new version of  Windows or   upgrade Windows to the latest version. To help you determine the deployment method that meets your needs, review [Scenarios to deploy enterprise operating systems with System Center Configuration Manager](../System Center Configuration Manager/Scenarios-to-deploy-enterprise-operating-systems-with-System-Center-Configuration-Manager.md).  You can choose from the following operating system deployment scenarios:  
  
-   [Upgrade Windows to the latest version with System Center Configuration Manager](../System Center Configuration Manager/Upgrade-Windows-to-the-latest-version-with-System-Center-Configuration-Manager.md)  
  
-   [Refresh an existing computer with a new version of Windows using System Center Configuration Manager](../System Center Configuration Manager/Refresh-an-existing-computer-with-a-new-version-of-Windows-using-System-Center-Configuration-Manager.md)  
  
-   [Install a new version of Windows on a new computer (bare metal) with System Center Configuration Manager](../System Center Configuration Manager/Install-a-new-version-of-Windows-on-a-new-computer--bare-metal--with-System-Center-Configuration-Manager.md)  
  
-   [Replace an existing computer and transfer settings with System Center Configuration Manager](../System Center Configuration Manager/Replace-an-existing-computer-and-transfer-settings-with-System-Center-Configuration-Manager.md)  
  
##  <a name="BKMK_OSDMethods"></a> Methods to deploy operating systems  
 There are several methods that you can use to deploy operating systems to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client computers.  
  
-   **PXE initiated deployments**: PXE-initiated deployments let client computers request a deployment over the network. In this method of deployment, the operating system image and a Windows PE boot image are sent to a distribution point that is configured to accept PXE boot requests. For more information, see [Use PXE to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-PXE-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md).  
  
-   **Make operating systems available in Software Center**: You can deploy an operating system and make it available in the Software Center. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients can initiate the operating system installation from Software Center. For more information, see [Replace an existing computer and transfer settings with System Center Configuration Manager](../System Center Configuration Manager/Replace-an-existing-computer-and-transfer-settings-with-System-Center-Configuration-Manager.md).  
  
-   **Multicast deployments**: Multicast deployments conserve network bandwidth by concurrently sending data to multiple clients instead of sending a copy of the data to each client over a separate connection. In this method of deployment, the operating system image is sent to a distribution point. This in turn deploys the image when client computers request the deployment. For more information, see [Use multicast to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-multicast-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md).  
  
-   **Bootable media deployments**: Bootable media deployments let you deploy the operating system when the destination computer starts. When the destination computer starts, it retrieves the task sequence, the operating system image, and any other required content from the network. Because that content is not included on the media, you can update the content without having to re-create the media. For more information, see [Create bootable media with System Center Configuration Manager](../System Center Configuration Manager/Create-bootable-media-with-System-Center-Configuration-Manager.md).  
  
-   **Stand-alone media deployments**: Stand-alone media deployments let you deploy operating systems in the following conditions:  
  
    -   In environments where it is not practical to copy an operating system image or other large packages over the network.  
  
    -   In environments without network connectivity or low bandwidth network connectivity.  
  
     For more information, see [Create stand-alone media with System Center Configuration Manager](../System Center Configuration Manager/Create-stand-alone-media-with-System-Center-Configuration-Manager.md).  
  
-   **Pre-staged media deployments**: Pre-staged media deployments let you deploy an operating system to a computer that is not fully provisioned. The pre-staged media is a Windows Imaging Format (WIM) file that can be installed on a bare-metal computer by the manufacturer or at an enterprise staging center that is not connected to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] environment.  
  
     Later in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] environment, the computer starts by using the boot image provided by the media, and then connects to the site management point for available task sequences that complete the download process. This method of deployment can reduce network traffic because the boot image and operating system image are already on the destination computer. You can specify applications, packages, and driver packages to include in the pre-staged media. For more information, see [Create prestaged media with System Center Configuration Manager](../System Center Configuration Manager/Create-prestaged-media-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_BootImages"></a> Boot images  
 A boot image in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is a Windows PE (WinPE) image that is used  during an operating system deployment. Boot images are used to start a computer in WinPE, which is a minimal operating system with limited components and services that prepare the destination computer for Windows installation. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides two boot images: One to support x86 platforms and one to support x64 platforms. These are considered default boot images. Boot images that you create and add to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] are considered custom images. Default boot images can be automatically replaced when you update [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For more information about boot images, see [Manage boot images with System Center Configuration Manager](../System Center Configuration Manager/Manage-boot-images-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_OSImages"></a> Operating  system images  
 Operating system images in Configuration Manager are stored in the Windows Imaging (WIM) file format and represent a compressed collection of reference files and folders that are required to successfully install and configure an operating system on a computer. For all operating system deployment scenarios, you must select an operating system image. You can use the default operating system image or build the operating system image from a reference computer that you configure. For more information, see [Manage operating system images with System Center Configuration Manager](../System Center Configuration Manager/Manage-operating-system-images-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_OSUpgradePackages"></a> Operating system upgrade packages  
 Operating system upgrade packages are used to upgrade an operating system and are setup-initiated operating system deployments. You import operating system upgrade packages to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] from a DVD or mounted ISO file. For more information, see [Manage operating system upgrade packages with System Center Configuration Manager](../System Center Configuration Manager/Manage-operating-system-upgrade-packages-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_OSDMedia"></a> Media to deploy operating systems  
 You can create several kinds of media that can be used to deploy operating systems. This includes capture media that is used to capture operating system images and stand-alone, pre-staged, and bootable media that is used to deploy an operating system. By using media, you can deploy operating systems on computers that do not have a network connection or that have a low bandwidth connection to your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. For more information about how to use media, see [Create task sequence media with System Center Configuration Manager](../System Center Configuration Manager/Create-task-sequence-media-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_DeviceDrivers"></a> Device drivers  
 You can install device drivers on destination computers without including them in the operating system image that is being deployed. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides a driver catalog that contains references to all the device drivers that you import into [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. The driver catalog is located in the **Software Library** workspace and consists of two nodes: **Drivers** and **Driver Packages**. The **Drivers** node lists all the drivers that you have imported into the driver catalog. You can use this node to discover the details about each imported driver, to change what driver package or boot image a driver belongs to, to enable or disable a driver, and more. For more information, see [Manage drivers in System Center Configuration Manager](../System Center Configuration Manager/Manage-drivers-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_OSDUserState"></a> Save and restore user state  
 When you deploy operating systems, you can save the user state from the destination computer, deploy the operating system, and then restore the user state after the operating systems is deployed. This process is typically used when you install the operating system on a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client computer.  
  
 The user state information is captured and restored by using task sequences. When the user state information is captured, the information can be stored in one of the following ways:  
  
-   You can store the user state data remotely by configuring a state migration point. The Capture task sequence sends the data to the state migration point. Then, after the operating system is deployed, the Restore task sequence retrieves the data and restores the user state on the destination computer.  
  
-   You can store the user state data locally to a specific location. In this scenario, the Capture task sequence copies the user data to a specific location on the destination computer. Then, after the operating system is deployed, the Restore task sequence retrieves the user data from that location.  
  
-   You can specify hard links that can be used to restore the user data to its original location. In this scenario, the user state data remains on the drive when the old operating system is removed. Then, after the operating system is deployed, the Restore task sequence uses the hard links to restore the user state data to its original location.  
  
 For more information [Manage user state in System Center Configuration Manager](../System Center Configuration Manager/Manage-user-state-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_UnknownComputer"></a> Deploy to unknown computers  
 You can deploy an operating system to computers that are not managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. There is no record of these computers in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. These computers are referred to as unknown computers. Unknown computers include the following:  
  
-   A computer where the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is not installed  
  
-   A computer that is not imported into [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
-   A computer that is not discovered by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
 For more information, see [Prepare for unknown computer deployments in System Center Configuration Manager](../System Center Configuration Manager/Prepare-for-unknown-computer-deployments-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_UDA"></a> Associate users with a computer  
 When you deploy an operating system, you can associate users with the destination computer to support user device affinity actions. When you associate a user with the destination computer, the administrative user can later perform actions on whichever computer is associated with that user, such as deploying an application to the computer of a specific user. However, when you deploy an operating system, you cannot deploy the operating system to the computer of a specific user. For more information, see [Associate users with a destination computer in System Center Configuration Manager](../System Center Configuration Manager/Associate-users-with-a-destination-computer-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_TaskSequences"></a> Use task sequences to automate steps  
 You can create task sequences to perform a variety of tasks within your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] environment. The actions of the task sequence are defined in the individual steps of the sequence. When the task sequence is run, the actions of each step are performed at the command-line level without requiring user intervention. You can use task sequences for the following:  
  
-   [Create a task sequence to install an operating system in System Center Configuration Manager](../System Center Configuration Manager/Create-a-task-sequence-to-install-an-operating-system-in-System-Center-Configuration-Manager.md)  
  
-   [Create a task sequence for non-operating system deployments with System Center Configuration Manager](../System Center Configuration Manager/Create-a-task-sequence-for-non-operating-system-deployments-with-System-Center-Configuration-Manager.md)  
  
-   [Create a task sequence to capture an operating system in System Center Configuration Manager](../System Center Configuration Manager/Create-a-task-sequence-to-capture-an-operating-system-in-System-Center-Configuration-Manager.md)  
  
-   [Create a task sequence to capture and restore user state in System Center Configuration Manager](../System Center Configuration Manager/Create-a-task-sequence-to-capture-and-restore-user-state-in-System-Center-Configuration-Manager.md)  
  
-   [Create a custom task sequence with System Center Configuration Manager](../System Center Configuration Manager/Create-a-custom-task-sequence-with-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Manage enterprise operating systems with System Center Configuration Manager](assetId:///c6b0ff4c-235a-4e4c-99c0-d14d202de478)