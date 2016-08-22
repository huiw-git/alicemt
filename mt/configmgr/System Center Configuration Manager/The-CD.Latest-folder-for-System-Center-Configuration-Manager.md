---
title: "The CD.Latest folder for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 8db92d67-5d9c-4e9c-80d0-ae6fa0dd4817
caps.latest.revision: 6
---
# The CD.Latest folder for System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] introduces a new update process which delivers updates to the product from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. To support this new method of updating Configuration Manager, a new folder is created named **CD.Latest** that contains a copy of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installation files for the updated version of your site.  

Beginning with update 1606, the CD.Latest folder contains a folder named **Redist** which contains the redistributable files that setup downloads and uses. These files are matched to the version of Configuration Manager files found in that CD.Latest folder. When you run Setup from a CD.Latest folder, you must use files that are matched to that version of Setup. To do so you can either direct Setup to download new and current files from Microsoft, or direct Setup to use the files from the Redist folder included in the CD.Latest folder. 

> [!TIP]
> If you have not yet installed version 1606, you must ensure redist files you use are current. If you have not downloaded redist files recently, plan to allow Setup to do so from Microsoft.   
  
 The following are scenarios that create or update the CD.Latest folder on a central administration site or primary site server:  
  
-   You install an update or hotfix from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console: The folder is created or updated in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installation folder.  
  
-   You run the built-in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] backup task: The folder is created or updated under the designated backup folder location.  
  
 The source files from the CD.Latest folder are supported for the following:  
  
1.  **Backup and recovery:** The CD.Latest folder contains source files you use to reinstall your site as part of a site recovery. To recover a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, your site backup must include the CD.Latest folder (the built-in site backup task automatically includes this folder as part of the site backup).  
  
    -   **When you reinstall a site as part of a site recovery,** you install the site from the CD.Latest folder included in your backup. This installs the site using the file versions that match your site backup and site database.  
  
        > [!IMPORTANT]  
        >  If you do not have the correct CD.Latest folder and its contents available, you cannot recover a site and it must be reinstalled.  
  
    -   When you do not have a CD.Latest folder but do have a working child primary site or central administration site, you can use that site as a reference site for a site recovery.  
  
2.  **To install a child primary site:** When you want to install a new child primary site below a central administration site that has installed one or more in-console updates, you must use Setup and the source files from the CD.Latest folder from the central administration site. When Setup runs from a copy of the CD.Latest folder from the central administration site, it uses installation source files that match the version of the central administration site. For more information see [Use the Setup Wizard to install sites](../System Center Configuration Manager/Use-the-Setup-Wizard-to-install-System-Center-Configuration-Manager-sites.md).  
  
3.  **To expand a stand-alone primary site:** When you are expanding a stand-alone primary site by installing a new central administration site, you must use Setup and the source files from the CD.Latest folder from the primary site to install the new central administration site. When run from a copy of the CD.Latest folder from the primary site, it uses installation source files that match the version of the primary site. For more information see [Expand a stand-alone primary site](../System Center Configuration Manager/Use-the-Setup-Wizard-to-install-System-Center-Configuration-Manager-sites.md#bkmk_expand)) in [Use the Setup Wizard to install sites](../System Center Configuration Manager/Use-the-Setup-Wizard-to-install-System-Center-Configuration-Manager-sites.md)
  
> [!IMPORTANT]  
>  The updated CD.Latest source files are not supported for:  
>   
>  -   Installing a new site for a new hierarchy  
> -   Upgrading a [!INCLUDE[cm5long](../System Center Configuration Manager/itokens/cm5long_md.md)] site to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]