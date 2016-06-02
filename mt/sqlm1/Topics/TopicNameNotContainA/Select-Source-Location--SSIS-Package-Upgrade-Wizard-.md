---
title: Select Source Location (SSIS Package Upgrade Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
---
# Select Source Location (SSIS Package Upgrade Wizard)
  Use the **Select Source Location** page to specify the source from which to upgrade packages.  
  
> [!NOTE]  
>  This page is only available when you run the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or at the command prompt.  
  
 **To run the SSIS Package Upgrade Wizard**  
  
-   [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](../../Topics\TopicNameNotContainA/Upgrade-Integration-Services-Packages-Using-the-SSIS-Package-Upgrade-Wizard.md)  
  
## Static Options  
 **Package source**  
 Select the storage location that contains the packages to be upgraded. This option has the values listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|**File System**|Indicates that the packages to be upgraded are in a folder on the local computer.<br /><br /> To have the wizard back up the original packages before upgrading those packages, the original packages must be stored in the file system. For more information, see How To Topic.|  
|**SSIS Package Store**|Indicates that the packages to be upgraded are in the package store. The package store consists of the set of file system folders that the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service manages. For more information, see [Package Management &#40;SSIS Service&#41;](../Topic/Package%20Management%20\(SSIS%20Service\).md).<br /><br /> Selecting this value displays the corresponding **Package source** dynamic options.|  
|**Microsoft SQL Server**|Indicates the packages to be upgraded are from an existing instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].<br /><br /> Selecting this value displays the corresponding **Package source** dynamic options.|  
  
 **Folder**  
 Type the name of a folder that contains the packages you want to upgrade or click **Browse** and locate the folder.  
  
 **Browse**  
 Browse to locate the folder that contains the packages you want to upgrade.  
  
## Package Source Dynamic Options  
  
### Package source \= SSIS Package Store  
 **Server**  
 Type the name of the server that has the packages to be upgraded, or select this server in the list.  
  
### Package source \= Microsoft SQL Server  
 **Server**  
 Type the name of the server that has the packages to be upgraded, or select this server from the list.  
  
 **Use Windows authentication**  
 Select to use Windows Authentication to connect to the server.  
  
 **Use SQL Server authentication**  
 Select to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication to connect to the server. If you use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, you must provide a user name and password.  
  
 **User name**  
 Type the user name that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication will use to connect to the server.  
  
 **Password**  
 Type the password that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication will use to connect to the server.  
  
## See Also  
 [Upgrade Integration Services Packages](../../Topics\TopicNameNotContainA/Upgrade-Integration-Services-Packages.md)  
  
  