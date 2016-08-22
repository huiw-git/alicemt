---
title: "Create a task sequence to upgrade an operating system in System Center Configuration Manager"
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
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: 12
---
# Create a task sequence to upgrade an operating system in System Center Configuration Manager
Use task sequences   in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to automatically upgrade  an operating system from Windows 7 or later to Windows 10 on a destination computer. You create a task sequence that references the operating system image that you want to install on the destination computer and any other additional content, such as applications or software updates that you want to install. The task sequence to upgrade an operating system is part of the [Upgrade Windows to the latest version with System Center Configuration Manager](../System Center Configuration Manager/Upgrade-Windows-to-the-latest-version-with-System-Center-Configuration-Manager.md) scenario.  
  
##  <a name="BKMK_UpgradeOS"></a> Create a task sequence to upgrade an operating system  
 To upgrade the operating system on computers to Windows 10, you can create a task sequence  and select **Upgrade an operating system from upgrade package** in the Create Task Sequence Wizard. The wizard will add the steps to upgrade the operating system, apply software updates, and install applications. Before  you create the  task sequence, the following must be in place:  
  
-   **Required**  
  
     The Windows 10 [operating system upgrade package](https://technet.microsoft.com/library/mt627916\(TechNet.10\).aspx) must be available in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
-   **Required (if used)**  
  
     [Software updates](https://technet.microsoft.com/library/mt612804\(TechNet.10\).aspx) must be synchronized in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
     [Applications](https://technet.microsoft.com/library/mt595707\(TechNet.10\).aspx) must be added to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
#### To create a task sequence that upgrades an operating system  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Software Library**.  
  
2.  In the **Software Library** workspace, expand **Operating Systems**, and then click **Task Sequences**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Task Sequence** to start the Create Task Sequence Wizard.  
  
4.  On the **Create a New Task Sequence** page, click **Upgrade an operating system from upgrade package**, and then click **Next**.  
  
5.  On the **Task Sequence Information** page, specify the following settings, and then click **Next**.  
  
    -   **Task sequence name**: Specify a name that identifies the task sequence.  
  
    -   **Description**: Specify a description of the task that is performed by the task sequence.  
  
6.  On the **Upgrade the  Windows Operating System** page, specify the following settings, and then click **Next**.  
  
    -   **Upgrade package**: Specify the upgrade package that contains the operating system upgrade source files. You can verify  that you have selected the correct upgrade package by looking at the information in the **Properties** pane. For more information, see [Manage operating system upgrade packages with System Center Configuration Manager](../System Center Configuration Manager/Manage-operating-system-upgrade-packages-with-System-Center-Configuration-Manager.md).  
  
    -   **Edition index**: If there are multiple operating system edition indexes available in the package, select the desired edition index. By default, the first item is selected.  
  
    -   **Product key**: Specify the product key for the Windows operating system to install. You can specify encoded volume license keys and standard product keys. If you use a non-encoded product key, each group of 5 characters must be separated by a dash (-). For example: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. When the upgrade is for a volume license edition, the product key is not required. You only need a product key when the upgrade is for a retail Windows edition.  
  
7.  On the **Include Updates** page, specify whether to install required software updates, all software updates, or no software updates, and then click **Next**. If you specify to install software updates, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs only those software updates that are targeted to the collections that the destination computer is a member of.  
  
8.  On the **Install Applications** page, specify the applications to install on the destination computer, and then click **Next**. If you specify multiple applications, you can also specify that the task sequence continues if the installation of a specific application fails.  
  
9. Complete the wizard.  
  
## Download Package Content task sequence step  
 The [Download Package Content](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_DownloadPackageContent) step can be used before the **Upgrade Operating System** step in the following scenarios :  
  
-   You use a single upgrade task sequence that can work with both x86 and x64 platforms. To do  this, include two **Download Package Content** steps in the **Prepare for Upgrade** group with conditions to detect the client architecture and download only the appropriate operating system upgrade package. Configure each **Download Package Content** step to use the same variable, and use the variable for the media path on the **Upgrade Operating System** step.  
  
-   To dynamically download an applicable driver package, use two **Download Package Content** steps with conditions to detect the appropriate hardware type for each driver package. Configure each **Download Package Content** step to use the same variable, and use the variable for the **Staged content** value in drivers section on the **Upgrade Operating System** step.  

   > [!NOTE]
   > When there is more than one package, Configuration Manager adds a numerical suffix to the variable name. For example, if you specify a variable of %mycontent% as a custom variable, this is the root for where all the referenced content is stored (which can be multiple packages). When you refer to the variable in a subsequence step, such as Upgrade Operating System, it is used with a numerical suffix. In this example, %mycontent01% or %mycontent02% where the number corresponds to the order in which the package is listed in this step.
  
## Optional post-processing task sequence steps  
 After you create the task sequence, you can add additional steps to uninstall applications with known compatibility issues, or add post-processing actions to run after the computer is restarted and the upgrade to Windows 10 is successful. Add these additional steps in the Post-Processing group of the task sequence.  
  
> [!NOTE]  
>  Because this task sequence is not linear, there are conditions on steps that can affect the results of the task sequence, depending on whether it successfully upgrades the client computer or if it has to roll back the client computer to the operating system version it started with.  
  
## Optional rollback task sequence steps  
 When something goes wrong with the upgrade process after the computer is restarted, Setup will roll back the upgrade to the previous operating system and the task sequence will continue with any steps in the Rollback group. After you create the task sequence, you can add optional steps to the Rollback group.  
  
## Folder and files removed after computer restart  
 When the task sequence to upgrade an operating system to Windows 10 and all other steps in the task sequence are complete, the post-processing and rollback scripts are not removed until the computer is restarted.  These script files do not contain sensitive information.  
  
## See Also  
 [Manage task sequences to automate tasks in System Center Configuration Manager](../System Center Configuration Manager/Manage-task-sequences-to-automate-tasks-in-System-Center-Configuration-Manager.md)