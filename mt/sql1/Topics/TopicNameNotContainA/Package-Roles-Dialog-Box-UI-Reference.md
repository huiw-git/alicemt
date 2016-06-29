---
title: Package Roles Dialog Box UI Reference
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
---
# Package Roles Dialog Box UI Reference
  Use the **Package Roles** dialog box, available in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/includes/ssManStudioFull_md.md)], to specify the database-level roles that have read access to the package and the database-level roles that have write access to the package. Database-level roles apply only to packages that are stored in the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] **msdb** database.  
  
 To learn more about the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] database-level roles and their permissions, see [Integration Services Roles &#40;SSIS Service&#41;](../../Topics/TopicNameNotContainA/Integration-Services-Roles--SSIS-Service-.md).  
  
 The roles listed in the dialog box are the current database roles of the **msdb** system database. If no roles are selected, the default [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] roles apply. By default, the reader role includes **db_ssisadmin**, **db_ssisoperator**, and the user who created the package. A user who is a member of one of these roles or created the packages can enumerate, view, export, and run packages. By default, the writer role includes **db_ssisadmin** and the user who created the package. A user who is a member of this role and the user who created the packages can import, delete, and change packages.  
  
 The **ownersid** column in the **sysssispackages** table lists the unique security identifier of the user who created the package.  
  
## Options  
 **Package Name**  
 Specify the name of the package.  
  
 **Reader Role**  
 Select a role in the list.  
  
 **Writer Role**  
 Select a role in the list  
  
## See Also  
 [Database-Level Roles](../../Topics/TopicNameNotContainA/Database-Level-Roles.md)   
 [Security Overview &#40;Integration Services&#41;](../../Topics/TopicNameNotContainA/Security-Overview--Integration-Services-.md)  
  
  