---
title: "Create stand-alone media with System Center Configuration Manager"
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
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
caps.latest.revision: 21
caps.handback.revision: 0
---
# Create stand-alone media with System Center Configuration Manager
Stand-alone media in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] contains everything that is required to deploy the operating system on a computer without a connection to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site or using the network. Use stand-alone media with the following operating system deployment scenarios:  
  
-   [Refresh an existing computer with a new version of Windows using System Center Configuration Manager](../System Center Configuration Manager/Refresh-an-existing-computer-with-a-new-version-of-Windows-using-System-Center-Configuration-Manager.md)  
  
-   [Install a new version of Windows on a new computer (bare metal) with System Center Configuration Manager](../System Center Configuration Manager/Install-a-new-version-of-Windows-on-a-new-computer--bare-metal--with-System-Center-Configuration-Manager.md)  
  
-   [Upgrade Windows to the latest version with System Center Configuration Manager](../System Center Configuration Manager/Upgrade-Windows-to-the-latest-version-with-System-Center-Configuration-Manager.md)  
  
 Stand-alone media includes the  task sequence that automates the steps to install the operating system and all other required content, including the boot image, operating system image, and device drivers. Because everything to deploy the operating system is stored on the stand-alone media, the disk space required for stand-alone media is significantly larger than the disk space required for other types of media. When you create stand-alone media on a central administration site, the client will retrieve its assigned site code from active directory. Stand-alone media created at child sites will automatically assign to the client the site code for that site.  
  
##  <a name="BKMK_CreateStandAloneMedia"></a> Create stand-alone media  
 Before you create stand-alone media by using the Create Task Sequence Media Wizard, be sure that the following conditions are met:  
  
|Task|Description|  
|----------|-----------------|  
|Create a task sequence to deploy an operating system|As part of the stand-alone media, you must specify the task sequence to deploy an operating system. For the steps to create a new task sequence, see [Create a task sequence to install an operating system in System Center Configuration Manager](../System Center Configuration Manager/Create-a-task-sequence-to-install-an-operating-system-in-System-Center-Configuration-Manager.md).<br /><br /> The following actions are not supported for stand-alone media:<br /><br /> -   The Auto Apply Drivers step in the task sequence. Automatic application of device drivers from the driver catalog is not supported, but you can choose the Apply Driver Package step to make a specified set of drivers available to Windows Setup.<br />-   Installing software updates.<br />-   Installing software before deploying the  operating system.<br />-   Associating users with the destination computer to support user device affinity.<br />-   Dynamic package installs via the Install Packages task.<br />-   Dynamic application installs via the Install Application task.<br /><br /> <br /><br /> If your task sequence to deploy an operating system includes  the [Install Package](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_InstallPackage) step and you create the stand-alone media at a central administration site, an error might occur. The central administration site does not have the necessary client configuration policies that are required to enable the software distribution agent during the execution of the task sequence. The following error might appear in the CreateTsMedia.log file:<br /><br /> `“WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)”`<br /><br /> For stand-alone media that includes an **Install Package** step, you must create the stand-alone media at a primary site that has the software distribution agent enabled or add a [Run Command Line](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_RunCommandLine) step after the [Setup Windows and ConfigMgr](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_SetupWindowsandConfigMgr) step and before the first **Install Package** step in the task sequence. The **Run Command Line** step runs a WMIC command to enable the software distribution agent before the first Install package step runs. You can use the following in your **Run Command Line** task sequence step:<br /><br /> **Command Line**: **WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE**|  
|Distribute all content associated with the task sequence|You must distribute all content that is required by the task sequence the  to at least one distribution point. This includes the boot image, operating system image, and other associated files. The wizard gathers the information from the distribution point when it creates the stand-alone media. You must have **Read** access rights to the content library on that distribution point.  For details, see [Distribute content referenced by a task sequence](../System Center Configuration Manager/Manage-task-sequences-to-automate-tasks-in-System-Center-Configuration-Manager.md#BKMK_DistributeTS).|  
|Prepare the removable USB drive|For a removable USB drive:<br /><br /> If you are going to use a removable USB drive, the USB  drive must be connected to the computer where the wizard is run and the USB drive must be detectable by Windows as a removal device. The wizard writes directly to the USB drive when it creates the media. Stand-alone media uses a FAT32 file system. You cannot create stand-alone media on a USB flash drive whose content contains a file over 4 GB in size.|  
|Create an output folder|For a CD/DVD set:<br /><br /> Before you run the Create Task Sequence Media Wizard to create media for a CD or DVD set, you must create a folder for the output files created by the wizard. Media that is created for a CD or DVD set is written as .iso files directly to the folder.|  
  
 Use the following procedure to create stand-alone media for a removable USB drive or a CD/DVD set.  
  
#### To create stand-alone media  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Task Sequences**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Task Sequence Media** to start the Create Task Sequence Media Wizard.  
  
4.  On the **Select Media Type** page, specify the following options, and then click **Next**.  
  
    -   Select **Stand-alone media**.  
  
    -   Optionally, if you want to allow the operating system to be deployed without requiring user input, select **Allow unattended operating system deployment**. When you select this option the user is not prompted for network configuration information or for optional task sequences. However, the user is still prompted for a password if the media is configured for password protection.  
  
5.  On the **Media Type** page, specify whether the media is a flash drive or a CD/DVD set, and then click configure the following:  
  
    > [!IMPORTANT]  
    >  Stand-alone media uses a FAT32 file system. You cannot create stand-alone media on a USB flash drive whose content contains a file over 4 GB in size.  
  
    -   If you select **USB flash drive**, specify the drive where you want to store the content.  
  
    -   If you select **CD/DVD set**, specify the capacity of the media and the name and path of the output files. The wizard writes the output files to this location. For example: **\\\servername\folder\outputfile.iso**  
  
         If the capacity of the media is too small to store the entire content, multiple files are created and you must store the content on multiple CDs or DVDs. When multiple media is required, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] adds a sequence number to the name of each output file that it creates. In addition, if you deploy an application along with the operating system and the application cannot fit on a single media, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] stores the application across multiple media. When the stand-alone media is run, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] prompts the user for the next media where the application is stored.  
  
        > [!IMPORTANT]  
        >  If you select an existing .iso image, the Task Sequence Media Wizard deletes that image from the drive or share as soon as you proceed to the next page of the wizard. The existing image is deleted, even if you then cancel the wizard.  
  
     Click **Next**.  
  
6.  On the **Security** page, enter a strong password to help protect the media, and then click **Next**. If you specify a password, the password is required to use the media.  
  
    > [!IMPORTANT]  
    >  On stand-alone media, only the task sequence steps and their variables are encrypted. The remaining content of the media is not encrypted, so do not include any sensitive information in task sequence scripts. Store and implement all sensitive information by using task sequence variables.  
  
7.  On the **Stand-Alone CD/DVD** page, specify the task sequence that deploys the operating system, and then click **Next**. The wizard lets you select only those task sequences that are associated with a boot image.  
  
8.  On the **Distribution Points** page, specify the distribution points that contain the content required by the task sequence, and then click **Next**.  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will only display distribution points that have the content. You must distribute all of the content associated with the task sequence (boot image, operating system image, etc.) to at least one distribution point before you can continue. After you distribute the content, you can either restart the wizard or remove any distribution points that you already selected  on this page, go to the previous page, and then back to the **Distribution Points** page to refresh the distribution point list. For more information about distributing content, see [Distribute content referenced by a task sequence](../System Center Configuration Manager/Manage-task-sequences-to-automate-tasks-in-System-Center-Configuration-Manager.md#BKMK_DistributeTS). For more information about distribution points and content management, see [Manage content and content infrastructure for System Center Configuration Manager](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md).  
  
    > [!NOTE]  
    >  You must have **Read** access rights to the content library on the distribution points.  
  
9. On the **Customization** page, specify the following information, and then click **Next**.  
  
    -   Specify the variables that the task sequence uses to deploy the operating system.  
  
    -   Specify any prestart commands that you want to run before the task sequence. Prestart commands are a script or an executable that can interact with the user in Windows PE before the task sequence runs to install the operating system. For more information about prestart commands for media, see [Prestart commands for task sequence media in System Center Configuration Manager](../System Center Configuration Manager/Prestart-commands-for-task-sequence-media-in-System-Center-Configuration-Manager.md).  
  
         Optionally, select **Files for the prestart command** to include any required files for the prestart command.  
  
        > [!TIP]  
        >  During task sequence media creation, the task sequence writes the package ID and prestart command-line, including the value for any task sequence variables, to the CreateTSMedia.log log file on the computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. You can review this log file to verify the value for the task sequence variables.  
  
10. Complete the wizard.  
  
 The stand-alone media files (.iso) are created in the destination folder. If you selected **Stand-Alone CD/DVD**, you can now copy the output files to a set of CDs or DVDs.  
  
##  <a name="BKMK_StandAloneMediaTSExample"></a> Example task sequence for stand-alone media  
 Use the following table as a guide as you create a task sequence to deploy an operating system using stand-alone media. The table will help you decide the general sequence for your task sequence steps and how to organize and structure those task sequence steps into logical groups. The task sequence that you create might vary from this sample and can contain more or fewer task sequence steps and groups.  
  
> [!NOTE]  
>  You must always use the Task Sequence Media Wizard to create stand-alone media.  
  
|Task Sequence Group or Step|Description|  
|---------------------------------|-----------------|  
|Capture File and Settings - **(New Task Sequence Group)**|Create a task sequence group. A task sequence group keeps similar task sequence steps together for better organization and error control.|  
|Capture Windows Settings|Use this task sequence step to identify the Microsoft Windows settings that are captured from the existing operating system on the destination computer prior to reimaging. You can capture the computer name, user and organizational information, and the time zone settings.|  
|Capture Network Settings|Use this task sequence step to capture network settings from the computer that receives the task sequence. You can capture the domain or workgroup membership of the computer and the network adapter setting information.|  
|Capture User Files and Settings - **(New Task Sequence Sub-Group)**|Create a task sequence group within a task sequence group. This sub-group contains the steps needed to capture user state data from the existing operating system on the destination computer prior to reimaging. Similar to the initial group that you added, this sub-group keeps similar task sequence steps together for better organization and error control.|  
|Set Local State Location|Use this task sequence step to specify a local location using the protected path task sequence variable. The user state is stored on a protected directory on the hard drive.|  
|Capture User State|Use this task sequence step to capture the user files and settings you want to migrate to the new operating system.|  
|Install Operating System - **(New Task Sequence Group)**|Create another task sequence sub-group. This sub-group contains the steps needed to install the operating system.|  
|Reboot to Windows PE or hard disk|Use this task sequence step to specify restart options for the computer that receives this task sequence. This step will display a message to the user indicating that the computer will be restarted so that the installation can continue.<br /><br /> This step uses the read-only **_SMSTSInWinPE** task sequence variable. If the associated value equals **false** the task sequence step will continue.|  
|Apply Operating System|Use this task sequence step to install the operating system image onto the destination computer. This step deletes all files on that volume (with the exception of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]-specific control files) and then applies all volume images contained in the WIM file to the corresponding sequential disk volume. You can also specify a **sysprep** answer file to configure which disk partition to use for the installation.|  
|Apply Windows Settings|Use this task sequence step to configure the Windows settings configuration information for the destination computer. The windows settings you can apply are user and organizational information, product or license key information, time zone, and the local administrator password.|  
|Apply Network Settings|Use this task sequence step to specify the network or workgroup configuration information for the destination computer. You can also specify if the computer uses a DHCP server or you can statically assign the IP address information.|  
|Apply Driver Package|Use this task sequence step to make all device drivers in a driver package available for use by Windows setup. All necessary device drivers must be contained on the stand-alone media.|  
|Setup Operating System - **(New Task Sequence Group)**|Create another task sequence sub-group. This sub-group contains the steps needed to install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.|  
|Setup Windows and ConfigMgr|Use this task sequence step to install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client software. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs and registers the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client GUID. You can assign the necessary installation parameters in the **Installation properties** window.|  
|Restore User Files and Settings - **(New Task Sequence Group)**|Create another task sequence sub-group. This sub-group contains the steps needed to restore the user state.|  
|Restore User State|Use this task sequence step to initiate the User State Migration Tool (USMT) to restore the user state and settings that were captured from the Capture User State Action to the destination computer.|  
  
## See Also  
 [Manage task sequences to automate tasks in System Center Configuration Manager](../System Center Configuration Manager/Manage-task-sequences-to-automate-tasks-in-System-Center-Configuration-Manager.md)