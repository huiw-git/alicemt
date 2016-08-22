---
title: "Manage operating system upgrade packages with System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-27
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
caps.latest.revision: 12
caps.handback.revision: 0
---
# Manage operating system upgrade packages with System Center Configuration Manager
An upgrade package in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] contains the Windows Setup source files that are used to upgrade an existing operating system on a computer. Use the following  sections manage operating system upgrade packages in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
  
-   [Add operating system upgrade packages to Configuration Manager](#BKMK_AddOSUpgradePkgs)  
  
-   [Distribute operating system images to a distribution point](#BKMK_DistributeBootImages)  
  
-   [Apply software updates to an operating system upgrade package](#BKMK_OSUpgradePkgApplyUpdates)  
  
##  <a name="BKMK_AddOSUpgradePkgs"></a> Add operating system upgrade packages to Configuration Manager  
 Before you can use an operating system upgrade package, you must add the package to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. Use the following procedure to add an operating system upgrade package  to a site.  
  
#### To add an operating system upgrade package  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Operating System upgrade packages**.  
  
3.  On the **Home** tab, in the **Create** group, click **Add Operating System Upgrade Package** to start the Add Operating System Upgrade Wizard.  
  
4.  On the **Data Source** page, specify the network path to the installation source files of the operating system upgrade package. For example, specify the UNC **\\\server\path** to where the installation source files are located.  
  
    > [!NOTE]  
    >  The installation source files contain Setup.exe and other files and folders to install the operating system.  
  
    > [!IMPORTANT]  
    >  Limit access to the  installation source files to prevent unwanted tampering.  
  
5.  On the **General** page, specify the following information, and then click **Next**. This information is useful for identification purposes when you have multiple operating system installers.  
  
    -   **Name**: Specify the name of the operating system installer.  
  
    -   **Version**: Specify the version of the operating system installer.  
  
    -   **Comment**: Specify a brief description of the operating system installer.  
  
6.  Complete the wizard.  
  
 You can now distribute the operating system installer to the distribution points that are accessed by your deployment task sequences.  
  
##  <a name="BKMK_DistributeBootImages"></a> Distribute operating system images to a distribution point  
 Operating system images are distributed to distribution points in the same way as you distribute other content. In most cases, you must distribute the operating system image to at least one distribution point before you deploy the operating system. For the steps to distribute an operating system image, see [Distribute content](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_dist).  
  
##  <a name="BKMK_OSUpgradePkgApplyUpdates"></a> Apply software updates to an operating system upgrade package  
 Beginning in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] version 1602, you can apply new software updates to the operating system image in your operating system upgrade package. Of course, before you can apply software updates to an upgrade package you must have your software updates infrastructure in place and have successfully synchronized software updates. For more information, see [Deploy and manage software updates in System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-software-updates-in-System-Center-Configuration-Manager.md).  
  
 You can apply applicable software updates to an upgrade package on a specified schedule. On the schedule that you specify, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] applies the software updates that you select to the operating system upgrade package, and then optionally distributes the updated upgrade package to distribution points. Information about the operating system upgrade package is stored in the site database, including the software updates that were applied at the time of the import. Software updates that have been applied to the upgrade package since it was initially added are also stored in the site database. When you start the wizard to apply software updates to the operating system upgrade package, the wizard retrieves a list of applicable software updates that have not yet been applied to the upgrade package for you to select. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] copies the software updates from the content library on the site server and applies the software updates to the operating system upgrade package.  
  
 Use the following procedure to apply software updates to an operating system upgrade package.  
  
#### To apply software updates to an operating system upgrade package  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Operating System upgrade packages**.  
  
3.  Select the operating system upgrade package to which to apply software updates.  
  
4.  On the **Home** tab, in the **Operating System Upgrade Packages** group, click **Schedule Updates** to start the wizard.  
  
5.  On the **Choose Updates** page, select the software updates to apply to the operating system image, and then click **Next**.  
  
6.  On the **Set Schedule** page, specify the following settings, and then click **Next**.  
  
    1.  **Schedule**: Specify the schedule for when the software updates are applied to the operating system image.  
  
    2.  **Continue on error**:  Select this option to continue to apply software updates to the image even when there is an error.  
  
    3.  **Distribute the image to distribution points**: Select this option to update the operating system image on distribution points after the software updates are applied.  
  
7.  On the **Summary** page, verify the information, and then click **Next**.  
  
8.  On the **Completion** page, verify that the software updates were successfully applied to the operating system image.  
  
## See Also  
 [Prepare for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Prepare-for-operating-system-deployment-in-System-Center-Configuration-Manager.md)