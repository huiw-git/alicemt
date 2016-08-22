---
title: "Use PXE to deploy Windows over the network with System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-12
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
caps.latest.revision: 19
caps.handback.revision: 0
---
# Use PXE to deploy Windows over the network with System Center Configuration Manager
PXE-initiated operating system deployments in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] let client computers request and deploy operating systems over the network. In this operating system deployment scenario, the operating system image and both the x86 and x64 Windows PE boot images are sent to a distribution point that is configured to accept PXE boot requests.  
  
> [!NOTE]  
>  When you create an operating system deployment that targets only  x64 BIOS  computers, both the x64 boot image and x86 boot image must be available on the distribution point.  
  
 You can use PXE-initiated operating system deployments in the following operating system deployment scenarios:  
  
-   [Refresh an existing computer with a new version of Windows using System Center Configuration Manager](../System Center Configuration Manager/Refresh-an-existing-computer-with-a-new-version-of-Windows-using-System-Center-Configuration-Manager.md)  
  
-   [Install a new version of Windows on a new computer (bare metal) with System Center Configuration Manager](../System Center Configuration Manager/Install-a-new-version-of-Windows-on-a-new-computer--bare-metal--with-System-Center-Configuration-Manager.md)  
  
 Complete the steps in one of the operating system deployment scenarios and then use the following sections to prepare for PXE-initiated deployments.  
  
##  <a name="BKMK_Configure"></a> Configure at least one distribution point to accept PXE requests  
 To deploy operating systems to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients that make PXE boot requests, you must use one or more distribution points that are configured to respond to the PXE boot requests.  For the steps to enable PXE on a distribution point, see [Configuring distribution points to accept PXE requests](../System Center Configuration Manager/Prepare-site-system-roles-for-operating-system-deployments-with-System-Center-Configuration-Manager.md#BKMK_PXEDistributionPoint).  
  
## Prepare a PXE-enabled boot image  
 To use PXE to deploy an operating system, you must have both x86 and x64 PXE-enabled boot images distributed to one or more PXE-enabled distribution points. Use the information to enable PXE on a boot image and distribute the boot image to distribution points:  
  
-   To enable PXE on a boot image, select  **Deploy this boot image from the PXE-enabled distribution point** from the **Data Source** tab in the boot image properties.  
  
-   If you change the properties for the boot image, re-distribute the boot image to distribution points. For more information, see [Distribute content](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_dist).  
  
##  <a name="BKMK_PXEExclusionList"></a> Create an exclusion list for PXE deployments  
 When you use PXE to deploy operating systems, you can create an exclusion list on each distribution point to  ignore PXE boot requests from computers that are in the exclusion list. The exclusion list contains MAC addresses of the computers that you want the distribution point to ignore. These computers will not receive the deployment task sequences that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses for PXE deployment.  
  
 Use the following steps to create the PXE exclusion list.  
  
#### To create the exclusion list  
  
1.  Create a text file on the distribution point that is enabled for PXE. As an example, name this text file **pxeExceptions.txt**.  
  
2.  Use a standard text editor, such as Notepad, and add the MAC addresses of the computers to be ignored by the PXE-enabled distribution point. Separate the MAC address values by colons, and enter each address on a separate line. For example: `01:23:45:67:89:ab`  
  
3.  Save the text file on the PXE-enabled distribution point site system server. The text file can be saved to any location on the server.  
  
4.  Edit the registry of the PXE-enabled distribution point to create a **MACIgnoreListFile** registry key that contains the string value of the full path to the location of the text file on the PXE-enabled distribution point site system server. Use the following registry path:  
  
     **HKLM\Software\Microsoft\SMS\DP**  
  
    > [!WARNING]  
    >  If you use the Registry Editor incorrectly, you might cause serious problems that might require you to reinstall the operating system. Microsoft cannot guarantee that you can solve problems that result from using the Registry Editor incorrectly. Use the Registry Editor at your own risk.  
  
     There is no need to restart the server after you make this registry change.  
  
## Configure deployment settings  
 To use a PXE-initiated operating system deployment, you must configure the deployment to make the operating system available for PXE boot requests. You can configure this on the **Deployment Settings** page of the Deploy Software Wizard or the **Deployment Settings** tab in the properties for the deployment.  For the **Make available to the following** setting, configure one of the following:  
  
-   Configuration Manager clients, media and PXE  
  
-   Only media and PXE  
  
-   Only media and PXE (hidden)  
  
##  <a name="BKMK_Deploy"></a> Deploy the task sequence  
 Deploy the operating system to a target collection. For more information, see [Deploy a task sequence](../System Center Configuration Manager/Manage-task-sequences-to-automate-tasks-in-System-Center-Configuration-Manager.md#BKMK_DeployTS). When you deploy operating systems by using PXE, you can configure whether the deployment is required or available.  
  
-   **Required deployment**: Required deployments will use PXE without any user intervention. The user will not be able to bypass the PXE boot. However, if the user cancels the PXE boot before the distribution point responds, the operating system will not be deployed.  
  
-   **Available deployment**: Available deployments require that the user is present at the destination computer so that they can press the F12 key to continue the PXE boot process. If the user is not present to press F12, the computer will boot into the current operating system or from the next available boot device.  
  
 You can re-deploy a required PXE deployment by clearing the status of the last PXE deployment assigned to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collection or a computer. This action resets the status of that deployment and re-deploys the most recent required deployments.  
  
> [!IMPORTANT]  
>  The PXE protocol is not secure. Ensure that the PXE server and the PXE client are located on a physically secure network, such as in a data center to prevent unauthorized access to your site.  

##  How is the boot image selected for clients booting with PXE?
When a client boots with PXE, Configuration Manager provides the client with a boot image to use. Starting in Configuration Manager version 1606, Configuration Manager uses a boot image with an exact architecture match if one is available. If a boot image with the exact architecture is not available, Configuration Manager uses a boot image with a compatible architecture. The following list provides details about how a boot image is selected for clients booting with PXE.
1. Configuration Manager looks in the site database for the system record that matches the MAC address or SMBIOS of the client that is trying to boot.
2. Configuration Manager looks for task sequences that are deployed to the system record found in step 1.
3. In the list of task sequences found in step 2, Configuration Manager looks for a boot image that matches the architecture of the client that is trying to boot. If a boot image is found with the same architecture, that boot image is used.

4. If a boot image is not found with the same architecuture, Configuration Manager looks for a boot image (from the list of task sequences found in step 2) that is compatible with the architecture of the client that is trying to boot. For example, a 64-bit client is compatible with 32-bit and 64-bit boot images. A 32-bit client is compatible with only 32-bit boot images. A UEFI client is compatible with only 64-bit boot images.

## See Also  
 [Methods to deploy enterprise operating systems using System Center Configuration Manager](../System Center Configuration Manager/Methods-to-deploy-enterprise-operating-systems-using-System-Center-Configuration-Manager.md)