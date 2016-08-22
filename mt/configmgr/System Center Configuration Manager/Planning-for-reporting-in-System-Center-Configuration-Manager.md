---
title: "Planning for reporting in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: ff920c84-d5c8-458c-b67f-bc7219b05690
caps.latest.revision: 6
---
# Planning for reporting in System Center Configuration Manager
Reporting in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] provides a set of tools and resources that help you use the advanced reporting capabilities of SQL Server Reporting Services. Use the following sections to help you plan for reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
##  <a name="BKMK_InstallReportingServicesPoint"></a> Determine where to install the Reporting Services Point  
 When you run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports at a site, the reports have access to the information in the site database in which it connects. Use the following sections to help you determine where to install the reporting services point and what data source to use.  
  
> [!NOTE]  
>  For more information about planning for site systems in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Add site system roles for System Center Configuration Manager](../System Center Configuration Manager/Add-site-system-roles-for-System-Center-Configuration-Manager.md).  
  
###  <a name="BKMK_SupportedSiteServers"></a> Supported site system servers  
 You can install the reporting services point on a central administration site and primary sites, and on multiple site systems at a site and at other sites in the hierarchy. The reporting services point is not supported on secondary sites. The first reporting services point at a site is configured as the default report server. You can add more reporting services points at a site, but the default report server at each site is actively used for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports. You can install the reporting services point on the site server or a remote site system. However, as a best practice for performance reasons, use Reporting Services on a remote site system server.  
  
###  <a name="BKMK_DataReplication"></a> Data replication considerations  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] classifies the data that it replicates as either global data or site data. Global data refers to objects that were created by administrative users and that are replicated to all sites throughout the hierarchy, while secondary sites receive only a subset of global data. Examples of global data include software deployments, software updates, collections, and role-based administration security scopes. Site data refers to operational information that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] primary sites and the clients that report to primary sites create. Site data replicates to the central administration site but not to other primary sites. Examples of site data include hardware inventory data, status messages, alerts, and the results from query-based collections. Site data is only visible at the central administration site and the primary site where the data originates.  
  
 Consider the following factors to help you determine where to install your reporting services points:  
  
-   A reporting services point with the central administration site database as its reporting data source has access to all global and site data in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. If you require reports that contain site data for multiple sites in a hierarchy, consider installing the reporting services point on a site system at the central administration site and use the central administration site’s database as the reporting data source.  
  
-   A reporting services point with the child primary site database as its reporting data source has access to global data and site data for only the local primary site and any child secondary sites. Site data for other primary sites in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy is not replicated to the primary site, and therefore Reporting Services cannot access it. If you require reports that contain site data for a specific primary site or global data, but you do not want the report user to have access to site data from other primary sites, install a reporting services point on a site system at the primary site and use the primary site’s database as the reporting data source.  
  
###  <a name="BKMK_NetworkBandwidth"></a> Network bandwidth considerations  
 Site system servers in the same site communicate with each other by using server message block (SMB), HTTP, or HTTPS, depending on how you configure the site. Because these communications are unmanaged and can occur at any time without network bandwidth control, review your available network bandwidth before you install the reporting services point role on a site system.  
  
> [!NOTE]  
>  For more information about planning for site systems, see [Add site system roles for System Center Configuration Manager](../System Center Configuration Manager/Add-site-system-roles-for-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_RoleBaseAdministration"></a> Planning for role-based administration for reports  
 Security for reporting is much like other objects in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] where you can assign security roles and permissions to administrative users. Administrative users can only run and modify reports for which they have appropriate security rights. To run reports in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you must have the **Read** right for the **Site** permission and the permissions configured for specific objects.  
  
 However, unlike other objects in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], the security rights that you set for administrative users in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console must also be configured in Reporting Services. When you configure security rights in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, the reporting services point connects to Reporting Services and sets appropriate permissions for reports. For example, the **Software Update Manager** security role has the **Run Report** and **Modify Report** permissions associated with it. Administrative users who are only assigned the **Software Update Manager** role can only run and modify reports for software updates. Reports for other objects are not displayed in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. The exception to this is that some reports are not associated with specific [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] securable objects. For these reports, the administrative user must have the **Read** right for the **Site** permission to run the reports and the **Modify** right for the **Site** permission to modify the reports.  
  
 Reports are fully enabled for role-based administration. The data for all reports included with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is filtered based on the permissions of the administrative user who runs the report. Administrative users with specific roles can only view information defined for their roles.  
  
 For more information about security rights for reporting, see [Configuring reporting in System Center Configuration Manager](../System Center Configuration Manager/Configuring-reporting-in-System-Center-Configuration-Manager.md).  
  
 For more information about role-based administration in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Configure role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Configure-role-based-administration-for-System-Center-Configuration-Manager.md).  
  
## Supplemental planning topics for reporting  
 Use the following additional topics to help you plan for reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
  
-   [Prerequisites for reporting in System Center Configuration Manager](../System Center Configuration Manager/Prerequisites-for-reporting-in-System-Center-Configuration-Manager.md)  
  
-   [Best practices for reporting in System Center Configuration Manager](../System Center Configuration Manager/Best-practices-for-reporting-in-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md)