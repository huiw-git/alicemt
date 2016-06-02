---
title: Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
---
# Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard
  You can upgrade packages that were created in earlier versions of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] format that [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] uses. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard to help in this process. Because you can configure the wizard to backup up your original packages, you can continue to use the original packages if you experience upgrade difficulties.  
  
 The [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard is installed when [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is installed.  
  
> [!NOTE]  
>  The [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard is available in the Standard, Enterprise, and Developer Editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 For more information about how to upgrade [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages, see [Upgrade Integration Services Packages](../../Topics\TopicNameNotContainA/Upgrade-Integration-Services-Packages.md).  
  
 The remainder of this topic describes how to run the wizard and back up the original packages.  
  
## Running the SSIS Package Upgrade Wizard  
 You can run the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], or at the command prompt.  
  
#### To run the wizard from SQL Server Data Tools  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], create or open an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project.  
  
2.  In Solution Explorer, right\-click the **SSIS Packages** node, and then click **Upgrade All Packages** to upgrade all the packages under this node.  
  
    > [!NOTE]  
    >  When you open an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains [!INCLUDE[ssISversion10](../../Token\Other/ssISversion10_md.md)] or later packages, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] automatically opens the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard.  
  
#### To run the wizard from SQL Server Management Studio  
  
-   In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], expand the **Stored Packages** node, and right\-click the **File System** or **MSDB** node, and then click **Upgrade Packages**.  
  
#### To run the wizard at the command prompt  
  
-   At the command prompt, run the SSISUpgrade.exe file from the **C:\\Program Files\\Microsoft SQL Server\\130\\DTS\\Binn** folder.  
  
## Backing Up the Original Packages  
 To back up the original packages, both the original packages and the upgraded packages must be stored in the same folder in the file system. Depending on how you run the wizard, this storage location might be automatically selected.  
  
-   When you run the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], the wizard automatically stores both the original packages and upgraded packages in the same folder in the file system.  
  
-   When you run the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or at the command prompt, you can specify different storage locations for the original and upgraded packages. To back up the original packages, make sure to specify that both the original and upgraded packages are stored in the same folder in the file system. If you specify any other storage options, the wizard will not be able to back up the original packages.  
  
 When the wizard backs up the original packages, the wizard stores a copy of the original packages in an **SSISBackupFolder** folder. The wizard creates this **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.  
  
#### To back up the original packages in SQL Server Management Studio or at the command prompt  
  
1.  Save the original packages to a location on the file system.  
  
    > [!NOTE]  
    >  The backup option in the wizard only works with packages that have been stored to the file system.  
  
2.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or at the command prompt, run the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard.  
  
3.  On the **Select Source Location** page of the wizard, set the **Package source** property to **File System**.  
  
4.  On the **Select Destination Location** page of the wizard, select **Save to source location** tosave the upgraded packages to the same location as the original packages.  
  
    > [!NOTE]  
    >  The backup option in the wizard is available only when the upgraded packages are stored in the same folder as the original packages.  
  
5.  On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.  
  
#### To back up the original packages in SQL Server Data Tools  
  
1.  Save the original packages to a location on the file system.  
  
2.  On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.  
  
    > [!WARNING]  
    >  The **Backup original packages** option is not displayed when you open a [!INCLUDE[ssISversion10](../../Token\Other/ssISversion10_md.md)] or later project in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], which automatically launches the wizard.  
  
3.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], run the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard.  
  
  