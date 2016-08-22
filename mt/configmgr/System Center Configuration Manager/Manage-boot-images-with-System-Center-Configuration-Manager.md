---
title: "Manage boot images with System Center Configuration Manager"
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
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
caps.latest.revision: 23
caps.handback.revision: 0
---
# Manage boot images with System Center Configuration Manager
A boot image in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is a [Windows PE (WinPE)](https://msdn.microsoft.com/library/windows/hardware/dn938389%28v=vs.85%29.aspx) image that is used  during an operating system deployment. Boot images are used to start a computer in WinPE, which is a minimal operating system with limited components and services that prepare the destination computer for Windows installation.  Use the following sections to manage boot images:  
  
-   [Default boot images](#BKMK_BootImageDefault)  
  
-   [Customize a boot image](#BKMK_BootImageCustom)  
  
-   [Add a boot image](#BKMK_AddBootImages)  
  
-   [Distribute boot images to a distribution point](#BKMK_DistributeBootImages)  
  
-   [Modify a boot image](#BKMK_ModifyBootImages)  
  
-   [Configure a boot image to deploy from a PXE-enabled distribution point](#BKMK_BootImagePXE)  
  
-   [Configure multiple languages for boot image deployment](#BKMK_BootImageLanguage)  
  
##  <a name="BKMK_BootImageDefault"></a> Default boot images  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides two default boot images: One to support x86 platforms and one to support x64 platforms. These images are stored in: \\\\*servername*>\SMS_<*sitecode*>\osd\boot\\<*x64 or i386*.  
  
 When you upgrade [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to a new version, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] might replace the default boot images, and customized boot images based on the default boot images,  in this location with updated files. The options that you configure on the default boot images at the site (such as optional components) are carried forward when the boot images are updated, including drivers. The source driver objects must be valid, including the driver source files, or the drivers will not be added to the updated boot images on the site. Other boot images that are not based on the default boot images, even if based on the same Windows ADK version, will not be updated. After boot images are updated, you will need to redistribute them to distribution points. Any media using the boot images will need to be recreated. If you do not want your customizeddefault boot images automatically updated, you should store them in a different location.  
  
 The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Trace Log Tool is added to all  boot images that you add to  the **Software Library**. When you are in WinPE, you can start the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Trace Log Tool by typing**CMTrace**from a command prompt.  
  
##  <a name="BKMK_BootImageCustom"></a> Customize a boot image  
 You can customize a boot image, or [Modify a boot image](#BKMK_ModifyBootImages), from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console when it is based on a Windows PE  version from the supported version of Windows ADK. When a site is upgraded with a new version and a new version of Windows ADK is installed, custom boot images (not in the default boot image location) are not updated with the new version of Windows ADK. When that happens, you will no longer be able to customize the boot images in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. However, they will continue to work as they did before the upgrade.  
  
 When a boot image is based on a different version of the Windows ADK installed on a site, you must customize the boot images  by using another method, such as using the Deployment Image Servicing and Management (DISM) command-line tool that is part of the Windows AIK and Windows ADK. For more information, see [Customize boot images with System Center Configuration Manager](../System Center Configuration Manager/Customize-boot-images-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_AddBootImages"></a> Add a boot image  
  
 During site installation, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically adds boot images that are based on a WinPE version from the supported version of the Windows ADK. Depending on the version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you might be able to add boot images based on a different WinPE version from the supported version the Windows ADK.  An error occurs when you try to add a  boot image that contains an unsupported version of WinPE.  
  
 The following provides the supported version of Windows ADK, the Windows PE version on which the boot image is based that can be customized from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and the Windows PE versions on which the boot image is based that you can customize by using DISM and then add the image to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   **Windows ADK version**  
  
     Windows ADK for Windows 10  
  
-   **Windows PE versions for boot images customizable from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console**  
  
     Windows PE 10  
  
-   **Supported Windows PE versions for boot images not customizable from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console**  
  
     Windows PE 3.1<sup>1</sup> and Windows PE 5  
  
     <sup>1</sup> You can only add a boot image to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] when it is based on Windows PE 3.1. Install the Windows AIK Supplement for Windows 7 SP1 to upgrade Windows AIK for Windows 7 (based on Windows PE 3) with the Windows AIK Supplement for Windows 7 SP1 (based on Windows PE 3.1). You can download Windows AIK Supplement for Windows 7 SP1 from the [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=5188).  
  
     For example, when you have [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can customize boot images from Windows ADK for Windows 10 (based on Windows PE 10) from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. However, while boot images based on Windows PE 5 are supported, you must customize them from a different computer and use the version of DISM that is installed with Windows ADK for Windows 8. Then, you can add the boot image to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. For more information with the steps to customize a boot image (add optional components and drivers), enable command support to the boot image, add the boot image to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and update distribution points with the boot image, see [Customize boot images with System Center Configuration Manager](../System Center Configuration Manager/Customize-boot-images-with-System-Center-Configuration-Manager.md). For more information about boot images, see [Manage boot images](../System Center Configuration Manager/Manage-boot-images-with-System-Center-Configuration-Manager.md).  
  
 Use the following procedure to manually add a boot image.  
  
#### To add a boot image  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Boot Images**.  
  
3.  On the **Home** tab, in the **Create** group, click **Add Boot Image** to start the Add Boot Image Wizard.  
  
4.  On the **Data Source** page, specify the following options, and then click **Next**.  
  
    -   In the **Path** box, specify the path to the boot image WIM file.  
  
         The specified path must be a valid network path in the UNC format. For example: \\\\<*servername*\\<*sharename*>\\<*bootimagename*>.wim.  
  
    -   Select the boot image from the **Boot Image** drop-down list. If the WIM file contains multiple boot images, select the  appropriate image.  
  
5.  On the **General**  page, specify the following options, and then click **Next**.  
  
    -   In the **Name** box, specify a unique name for the boot image.  
  
    -   In the **Version** box, specify a version number for the boot image.  
  
    -   In the **Comment** box, specify a brief description of how the boot image is used.  
  
6.  Complete the wizard.  
  
 The boot image is now listed in the **Boot Image** node of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. However, before you can use the boot image to deploy an operating system you must distribute the boot image to distribution points, distribution point groups, or to collections that are associated with distribution point groups.  
  
> [!NOTE]  
>  When you select the **Boot Image** node in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, the **Size (KB)** column displays the decompressed size for each boot image. However, when [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sends a boot image over the network, it sends a compressed copy of the image, which is typically much smaller than the size listed in the **Size (KB)** column.  
  
##  <a name="BKMK_DistributeBootImages"></a> Distribute boot images to a distribution point  
 Boot images are distributed to distribution points in the same way as you distribute other content. In most cases, you must distribute the boot image to at least one distribution point before you deploy an operating system and before you create media.  
  
> [!NOTE]  
>  To use PXE to deploy an operating system, consider the following before you distribute the boot image:  
>   
>  -   The distribution point must be configured to accept PXE requests.  
> -   You must distribute both an x86 and an x64 PXE-enabled boot image to at least one PXE-enabled distribution point.  
> -   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] distributes the boot images to the **RemoteInstall** folder on the PXE-enabled distribution point.  
>   
>  For more information about using PXE to deploy operating systems, see [Use PXE to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-PXE-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md).  
  
 For the steps to distribute a boot image, see [Distribute content](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_dist).  
  
##  <a name="BKMK_ModifyBootImages"></a> Modify a boot image  
 You can add or remove device drivers to the image or edit the properties associated with the boot image. The device drivers that you add or remove can include network adapters or mass storage device drivers. Consider the following factors when you modify boot images:  
  
-   You must import and enable the device drivers in the device driver catalog before you can add them to the boot image.  
  
-   When you modify a boot image, the boot image does not change any of the associated packages that the boot image references.  
  
-   After you make changes to a boot image, you must **update** the boot image on the distribution points that already have the boot image so that the most current version of the boot image is available. For more information, see [Manage content you have distributed](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#bkmk_manage).  
  
 Use the following procedure to modify a boot image.  
  
#### To modify the properties of a boot image  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Boot Images**.  
  
3.  Select the boot image that you want to modify.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties** to open the **Properties** dialog box for the boot image.  
  
5.  Set any of the following settings to change the behavior of the boot image:  
  
    -   On the **Images** tab, if you have changed the properties of the boot image by using an external tool, click **Reload**.  
  
    -   On the **Drivers** tab, add the Windows device drivers that are required to boot WinPE. Consider the following when you add device drivers:  
  
        -   Select  
                                    **Hide drivers that do not match the architecture of the boot image** to only display only drivers for the architecture of the boot image. The architecture is based on the architecture reported in the .INF from the manufacturer.  
  
        -   Select **Hide drivers that are not in a storage or network class (for boot images)** to only display storage and network drivers, and hide other drivers that are not typically needed for boot images, such as a video driver or modem driver.  
  
        -   Select **Hide drivers that are not digitally signed** to hide drivers that are not digitally signed.  
  
        -   As a best practice, add only NIC and Mass Storage Drivers to the boot image unless there are requirements for other drivers to be part of WinPE.  
  
        -   Because WinPE already comes with many drivers built in, add only NIC and Mass Storage Drivers that are not supplied by WinPE.  
  
        -   Make sure that the drivers that you add to the boot image  match the architecture of the boot image.  
  
        > [!NOTE]  
        >  You must import device drivers into the drivers catalog before you add them to a boot image. For information about how to import device drivers, see [Manage drivers in System Center Configuration Manager](../System Center Configuration Manager/Manage-drivers-in-System-Center-Configuration-Manager.md).  
  
    -   On the **Customization** tab, select any of the following settings:  
  
        -   Select the **Enable Prestart Commands** check box to specify a command to run before the task sequence is run. When prestart commands are enabled, you can then specify the command line that is run, whether support files are required to run the command, and the source location of those support files.  
  
            > [!WARNING]  
            >  You must add **cmd /c** to the start of the command line. If you do not specify **cmd /c**,   the  command will not close after it runs. The deployment continues to wait for the command to finish and  will not start any other configured commands or actions.  
  
            > [!TIP]  
            >  During task sequence media creation, the task sequence writes the package ID and prestart command-line, including the value for any task sequence variables, to the CreateTSMedia.log log file on the computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. You can review this log file to verify the value for the task sequence variables.  
  
        -   Set the **Windows PE Background** settings to specify whether you want to use the default WinPE background or a custom background.  
  
        -   Select **Enable command support (testing only)** to open a command prompt by using the **F8** key while the boot image is deployed. This is useful for troubleshooting while you are testing your deployment. Using this setting in a production deployment is not advised.  
  
        -   Configure the Windows PE scratch space, which is temporary storage (RAM drive) used by WinPE. For example, when an application is run within WinPE and needs to write temporary files, WinPE redirects the files to the scratch space in memory to simulate the presence of a hard disk. By default, WinPE allocates 32 megabytes (MB) of writeable memory.  
  
    -   On the **Data Source** tab, update any of the following settings:  
  
        -   Set **Image path** and **Image index** to change the source file of the boot image.  
  
        -   Select **Update distribution points on a schedule** to create a schedule for when the boot image is updated.  
  
        -   Select **Persist content in client cache** if you do not want the content of this package to age out of the client cache to make room for other content.  
  
        -   Select **Enable binary differential replication** to specify that only changed files are distributed when the boot image package is updated on the distribution point. This setting minimizes the network traffic between sites, especially when the boot image package is large and the changes are relatively small.  
  
        -   Select **Deploy this boot image from the PXE-enabled distribution point** if the boot image is used in a PXE-enabled deployment.  
  
            > [!NOTE]  
            >  For more information, see [Use PXE to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-PXE-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md).  
  
    -   On the **Data Access** tab, select any of the following settings:  
  
        -   Set the **Package share settings** if you want clients to install the content in this package from the network.  
  
        -   Set the **Package update settings** to specify how you want [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to disconnect users from the distribution point. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] might be unable to update the boot image when users are connected to the distribution point.  
  
    -   On the **Distribution Settings** tab, select any of the following settings:  
  
        -   In the **Distribution priority** list, specify the priority level that you want [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to use when multiple packages are distributed to the same distribution point.  
  
        -   Select **Distribute the content for this package to preferred distribution points** if you want to enable on-demand content distribution to preferred distribution points. When this setting is enabled, the management point distributes the content to all preferred distribution points when a client requests the content for the package and the content is not available on any preferred distribution points.  
  
        -   Set the **Prestaged distribution point settings** to specify how you want the boot image to be distributed to distribution points that are enabled for prestaged content.  
  
            > [!NOTE]  
            >  For more information about prestaged content, see [Prestage content](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md#BKMK_PrestageContent).  
  
    -   On the **Content Locations** tab, select the distribution point or distribution point group and perform any of the following actions:  
  
        -   Click **Redistribute** to distribute the boot image to the selected distribution point or distribution point group again.  
  
        -   Click **Validate** to check the integrity of the boot image package on the selected distribution point or distribution point group.  
  
    -   On the **Optional Components** tab, specify the components that are added to Windows PE for use with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For more information about available optional components, see [WinPE: Add packages (Optional Components Reference)](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx).  
  
    -   On the **Security** tab, select an administrative user and change the operations that they can perform.  
  
6.  After you have configured the properties, click **OK**.  
  
##  <a name="BKMK_BootImagePXE"></a> Configure a boot image to deploy from a PXE-enabled distribution point  
 Before you  can use a boot image for a PXE operating system deployment, you must configure the boot image to deploy from a PXE-enabled distribution point.  
  
#### To configure a boot image to deploy from a PXE-enabled distribution point  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Boot Images**.  
  
3.  Select the boot image that you want to modify.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties** to open the **Properties** dialog box for the boot image.  
  
5.  On the **Data Source** tab, select **Deploy this boot image from the PXE-enabled distribution point**.  
  
    > [!NOTE]  
    >  For more information, see [Use PXE to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-PXE-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md).  
  
6.  After you have configured the properties, click **OK**.  
  
##  <a name="BKMK_BootImageLanguage"></a> Configure multiple languages for boot image deployment  
 Boot images are language neutral. This allows you to use one boot image that will display the task sequence text in multiple languages, while in WinPE,  if you include the appropriate language support from the Windows PE Optional Components and set the appropriate task sequence variable to indicate which language can be displayed. The language of the operating system that you deploy is independent from the language that is displayed when in WinPE, regardless of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] version. The language that is displayed to the user is determined as follows:  
  
-   When a user runs the task sequence from an existing operating system, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically uses the language configured for the user. When the task sequence automatically runs as the result of a mandatory deployment deadline, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses the language of the operating system.  
  
-   For operating system deployments that use PXE or media, you can set the language ID value in the SMSTSLanguageFolder variable as part of a prestart command. When the computer boots to WinPE, messages are displayed in the language that you specified in the variable. If there is an error accessing the language resource file in the specified folder or you do not set the variable, messages are displayed in the WinPE language.  
  
    > [!NOTE]  
    >  When the media is protected with a password, the text that prompts the user for the password is always displayed in the WinPE language.  
  
 Use the following procedure to set the WinPE language for PXE or media-initiated operating system deployments.  
  
#### To set the Windows PE language for a PXE or media-initiated operating system deployment  
  
1.  Verify that the appropriate task sequence resource file (tsres.dll) is in the corresponding language folder on site server before you update the boot image. For example, the English resource file is in the following location:  <*ConfigMgrInstallationFolder*>\OSD\bin\x64\00000409\tsres.dll.  
  
2.  As part of your prestart command, set the SMSTSLanguageFolder environment variable to the appropriate language ID. The language ID must be specified by using decimal and not hexadecimal. For example, to set the language ID to English, you would specify a decimal value of 1033 instead of the hexadecimal value of 00000409 used for the folder name.  
  
## See Also  
 [Prepare for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Prepare-for-operating-system-deployment-in-System-Center-Configuration-Manager.md)