---
title: "Interoperability between different versions of System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
caps.latest.revision: 8
---
# Interoperability between different versions of System Center Configuration Manager
It is supported to install and operate multiple, independent hierarchies of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] on the same network. However, because different hierarchies of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] do not interoperate outside of migration, each hierarchy requires configurations to prevent conflicts between them. Additionally, you can make certain configurations to help resources that you manage to interact with the site systems from the correct hierarchy.  
  
 The following sections provide information about using different versions of Configuration Manager on the same network:  
  
-   [Interoperability between System Center Configuration Manager and earlier product versions](#BKMK_SupConfigInterop)  
  
-   [Interoperability for the Configuration Manager Console](#BKMK_ConsoleInterop)  
  
-   [Configuration Manager limitations in a mixed-version hierarchy](#bkmk_mixed)  
  
##  <a name="BKMK_SupConfigInterop"></a> Interoperability between System Center Configuration Manager and earlier product versions  
 Except during the process of upgrade from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] or from one [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] version to a newer version (using in-console updates), sites of different versions  cannot co-exist in the same hierarchy.  
  
 Because you can deploy a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site and hierarchy side-by-side with an existing [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] site or hierarchy, plan to prevent clients from either version from trying to join a site from the other. For example, if two or more [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchies have overlapping boundaries (See [About overlapping boundaries](../System Center Configuration Manager/Define-site-boundaries-and-boundary-groups-for-System-Center-Configuration-Manager.md#BKMK_BoundaryOverlap)) that include the same network locations, its a best practice to assign each new client to a specific site instead of using automatic site assignment. For information about automatic site assignment in [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)], see [How to assign clients to a site in System Center Configuration Manager](../System Center Configuration Manager/How-to-assign-clients-to-a-site-in-System-Center-Configuration-Manager.md).  
  
 Additionally, it is not supported to install a client from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] on a computer that hosts a site system role from [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], nor to install a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] client on a computer that hosts a site system role from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)].  
  
 Similarly, the following clients and the following Virtual Private Network (VPN) connection are not supported:  
  
-   Any [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or earlier computer client version  
  
-   Any [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or earlier device management client  
  
-   Windows CE Platform Builder device management client (any version)  
  
-   System Center Mobile Device Manager VPN connection  
  
###  <a name="BKMK_SupConfigSiteAssignment"></a> Client site assignment considerations  
 [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] clients can be assigned to only a single primary site. When automatic site assignment is used to assign clients to a site during client installation, and more than one boundary group includes the same boundary, and the boundary groups have different assigned sites, the actual site assignment of a client cannot be predicted.  
  
 If boundaries overlap across multiple [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites and hierarchies, clients might not assign to the site you expect,  or might not get assigned to a site at all.  
  
 [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] clients check the version of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site before they complete site assignment and cannot assign to a pervious version when site if boundaries overlap. However, [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] clients might incorrectly assign to a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site.  
  
 To prevent clients from unintentionally being assigned to a the wrong site when two hierarchies have overlapping boundaries, configure [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client installation parameters to assign clients to a specific site.  
  
##  <a name="bkmk_mixed"></a> Configuration Manager limitations  in a mixed-version hierarchy  
 When your in the process of upgrading a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site, there are times when different sites will be at different versions.  For example, you might upgrade a central administration site to a new version but due to site maintenance windows, one or more primary sites might not upgrade until a later time and date.  
  
 When different sites in a single hierarchy run different versions, some functionality is not available. This can affect how you manage [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] objects in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and what functionality is available to clients. Typically, functionality from the newer version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is not accessible at sites or to clients that run a lower service pack version.  
  
### Limitations when upgrading  Configuration Manager  
  
|Object|Details|  
|------------|-------------|  
|Network access account|**When upgrading from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:** When you use a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console connected to a  central administration site that has updated to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to view the network access account details, the console does not display details for accounts that are configured at a primary site that runs [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)]. After the primary site upgrades to the same version as the central administration site, the account details will be visible in the console.<br /><br /> **When upgrading between [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] versions:** When you use a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console connected to a  central administration site that has updated to a new version of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to view the network access account details, the console does not display details for accounts that are configured at a primary site that runs a previous version. After the primary site upgrades to the same version as the central administration site, the account details will be visible in the console.|  
|Boot images for operating system deployment|**When upgrading from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:**  When the top-level site of a hierarchy upgrades to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], the default boot images are automatically updated to Windows ADK 10-based boot images. Use these boot images only for deployments to clients at [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] sites. For more information, see [Planning for operating system deployment interoperability in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-operating-system-deployment-interoperability-in-System-Center-Configuration-Manager.md).<br /><br /> **When upgrading between [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] versions:** So long as new versions of cm6long do not update the version of the Windows ADK in use, there is not affect on boot images.|  
|New task sequence steps|When you create a task sequence that contains a task sequence step introduced in one version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] that is not available in an earlier version, you might encounter the following issues:<br /><br /> --   An error occurs when you try to edit the task sequence from a site running a previous version of Configuration Manager.<br /><br /> -- The task sequence will not run on a computer that runs a previous version of the Configuration Manager client.|  
|Client to down-level management point communications|A [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client that communicates with a management point from a site that runs a lower version than the client can only use functionality that the down-level version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports. For example, if you deploy content from a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site that recently updated to a client that communicates with a management point that has not yet upgraded to that version, that client cannot use new functionality from the latest version.|  
  
##  <a name="BKMK_ConsoleInterop"></a> Interoperability for the Configuration Manager Console  
 The following table contains information about the use of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console in an environment that has a mix of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] versions.  
  
|Interoperability environment|More information|  
|----------------------------------|----------------------|  
|An environment with both [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]|To manage a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, both the console and the site the console connects to must run the same version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For example, you cannot use a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] console to manage a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site, or vice versa.<br /><br /> It is not supported to install both the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] console and the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console on the same computer.|  
|An environment with multiple versions of System Center Configuration Manager|[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] does not support installing more than a single [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console on a computer. To use multiple consoles that are specific to different versions of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you must install the different consoles on separate computers.<br /><br /> During the process of upgrading sites in a hierarchy, you can connect a console to a site that runs a newer version and view information about other sites in that hierarchy. However, this configuration is not recommended as it is possible that differences between the console version and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site version can result in data issues, and some features that are available in the latest product version will not be available in the console.|  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)