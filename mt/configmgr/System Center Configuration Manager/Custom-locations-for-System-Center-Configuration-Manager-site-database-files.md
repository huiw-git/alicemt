---
title: "Custom locations for System Center Configuration Manager site database files"
ms.custom: na
ms.date: 2016-07-22
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
caps.latest.revision: 3
---
# Custom locations for System Center Configuration Manager site database files
 [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] supports custom locations for SQL Server database files.  
  
> [!NOTE]  
>  The option to specify non-default file locations is not available when you use a SQL Server cluster.  
  
 **During Setup** of a new primary site or central administration site, you can:  
  
-   Specify non-default file locations for the site database: [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup then creates the site database using these locations.  
  
-   Specify the use of a pre-created SQL Server database that uses custom file locations:  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup then uses that pre-created database and its pre-configured file locations.  
  
 **After Setup** you can change the location of the site database files. This requires you to stop the site and edit the file location in SQL Server:  
  
-   On the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server, stop the **SMS_Executive** service.  
  
-   Follow the documentation for the version of SQL Server that you use to guide you on how to move a user database. For example, if you use SQL Server 2014, see [Move User Databases](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) on TechNet.  
  
-   After you complete the database file move, restart the SMS_Executive service on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server.  
  
## See Also
 [Configure sites and hierarchies](../System Center Configuration Manager/Configure-sites-and-hierarchies-for-System-Center-Configuration-Manager.md)
 