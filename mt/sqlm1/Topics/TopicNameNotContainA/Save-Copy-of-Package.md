---
title: Save Copy of Package
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
---
# Save Copy of Package
  Use the **Save Copy of Package** dialog box, available in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], to save a copy of an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package from [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to a different location and, optionally, modify the protection level of the package.  
  
## Options  
 **Package location**  
 Select the type of storage location in which to save the package copy. The following options are available:  
  
 **SQL Server**  
  
 **File System**  
  
 **SSIS Package Store**  
  
 **Server**  
 Type a server name or select a server from the list. This option is available only if the storage location is **SQL Server** or **SSIS Package Store**.  
  
 **Authentication**  
 Select Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. This option is available only if the storage location is [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!IMPORTANT]  
>  Whenever possible use Windows Authentication.  
  
 **Authentication type**  
 Select an authentication type.  
  
 **User name**  
 If using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, provide a user name.  
  
 **Password**  
 If using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, provide a password.  
  
 **Package path**  
 Type the package path, or click the browse **\(…\)** button and locate the folder in which to store the package.  
  
 **Protection level**  
 Click the browse **\(…\)** button and update the protection level in the **Package Protection Level** dialog box. For more information, see [Package and Project Protection Level Dialog Box](../../Topics\TopicNameNotContainA/Package-and-Project-Protection-Level-Dialog-Box.md).  
  
## See Also  
 [Import Package Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Import-Package-Dialog-Box-UI-Reference.md)   
 [Export Package Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Export-Package-Dialog-Box-UI-Reference.md)   
 [Save Packages](../../Topics\TopicNameNotContainA/Save-Packages.md)   
 [Import and Export Packages &#40;SSIS Service&#41;](../Topic/Import%20and%20Export%20Packages%20\(SSIS%20Service\).md)  
  
  