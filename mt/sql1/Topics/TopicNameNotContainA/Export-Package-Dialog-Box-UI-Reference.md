---
title: "Export Package Dialog Box UI Reference"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Export Package Dialog Box UI Reference
Use the **Export Package** dialog box, available in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], to export a [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package to a different location and optionally, modify the protection level of the package.  
  
## Options  
 **Package location**  
 Select the type of storage to export the package to. The following options are available:  
  
 **SQL Server**  
  
 **File System**  
  
 **SSIS Package Storage**  
  
 **Server**  
 Type a server name or select a server from the list.  
  
 **Authentication**  
 Select Windows Authentication or [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication. This option is available only if the storage location is [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
> [!IMPORTANT]  
>  Whenever possible, use Windows Authentication.  
  
 **Authentication type**  
 Select an authentication type.  
  
 **User name**  
 If using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication, provide a user name.  
  
 **Password**  
 If using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication, provide a password.  
  
 **Package path**  
 Type the package path, or click the browse button **(…)** and locate the folder in which to store the package.  
  
 **Protection level**  
 Click the browse button **(…)** and update the protection level in the **Package Protection Level** dialog box. For more information, see [Package and Project Protection Level Dialog Box](../../Topics/TopicNameNotContainA/Package-and-Project-Protection-Level-Dialog-Box.md).  
  
## See Also  
 [Save Copy of Package](../../Topics/TopicNameNotContainA/Save-Copy-of-Package.md)   
 [Import Package Dialog Box UI Reference](../../Topics/TopicNameNotContainA/Import-Package-Dialog-Box-UI-Reference.md)   
 [Save Packages](../../Topics/TopicNameNotContainA/Save-Packages.md)   
 [Import and Export Packages (SSIS Service)](../../Topics/TopicNameNotContainA/Import-and-Export-Packages--SSIS-Service-.md)