---
title: Folder and File Permissions (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
robots: noindex,nofollow
---
# Folder and File Permissions (Master Data Services)
  When you install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], folders and files are installed in the file system at the installation path you specify for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] shared features. If you use the default installation path for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] shared features, the installation path for [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] is *drive*:\\Program Files\\Microsoft SQL Server\\130\\Master Data Services. Although you can change the shared features installation path, be aware of permissions that are inherited from the parent folder and permissions that are explicitly set for [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
## Inherited Permissions  
 The **Microsoft SQL Server** folder, the **Master Data Services** folder, and most subfolders and files inherit permissions from the parent folder specified in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. If you choose the default installation location, the parent folder that permissions are inherited from is *drive*:\\Program Files. The following table describes the default permissions for **Program Files**.  
  
> [!NOTE]  
>  If you modify default permissions for **Program Files**, or you choose a different installation location, the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] folders and files inherit permissions from their parent folder accordingly, and the permissions might differ from those described in the following table.  
  
###### Program Files Default Permissions  
  
|Group or account name|Permissions|  
|---------------------------|-----------------|  
|CREATOR OWNER|Special permissions|  
|SYSTEM|Special permissions|  
|Administrators|Special permissions|  
|Users|Read & execute, List folder contents, Read|  
|TrustedInstaller|List folder contents, Special permissions|  
  
## Explicit Permissions  
 The **MDSTempDir** folder and the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] Web.config file \(in the **WebApplication** folder\) do not inherit permissions. They have permissions that are set explicitly when you install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], regardless of the installation path you choose. Do not modify these permissions.  
  
###### MDSTempDir Permissions  
  
|Group or account name|Permissions|  
|---------------------------|-----------------|  
|SYSTEM|Modify, Read & execute, List folder contents, Read, Write|  
|Administrators|Modify, Read & execute, List folder contents, Read, Write|  
|MDS\_ServiceAccounts|Modify, Read & execute, List folder contents, Read, Write|  
  
###### Web.config Permissions  
  
|Group or account name|Permissions|  
|---------------------------|-----------------|  
|SYSTEM|Full control, Modify, Read & execute, Read, Write|  
|Administrators|Full control, Modify, Read & execute, Read, Write|  
|MDS\_ServiceAccounts|Read & execute, Read|  
  
 For more information about the contents of the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] Web.config file, see [Web Configuration Reference &#40;Master Data Services&#41;](../Topic/Web%20Configuration%20Reference%20\(Master%20Data%20Services\).md).  
  
## See Also  
 [Install Master Data Services](../../Topics\TopicNameNotContainA/Install-Master-Data-Services.md)  
  
  