---
title: "Configure sites and hierarchies for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 9efb4061-f642-48bd-8332-3357ff5b3118
caps.latest.revision: 15
---
# Configure sites and hierarchies for System Center Configuration Manager
After you install your first [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site or add additional sites to your hierarchy, use the following checklist to ensure you consider the most common configurations that affect both sites and hierarchies.  
  
## Checklist of common configurations for new and additional sites  
 In most deployments you will not need to configure the following options in any specific order:  
  
-   Some options build upon each other, such Active Directory Forest Discovery, boundaries,  and boundary groups.  
  
-   Several configurations have default values you can use without configuration changes, at least temporarily.  
  
-   Other configurations, like boundary groups and distribution point groups, require you to configure them before you can use them.  
  
|Action|Details|  
|------------|-------------|  
|Configure role-based administration|Role-based administration is how you to segregate administrative assignments to control which administrative users can view and manage different objects and data in your Configuration Manager environment.<br /><br /> Configurations for role-based administration are shared with all sites in a hierarchy.   <br />See [Configure role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Configure-role-based-administration-for-System-Center-Configuration-Manager.md)|  
|Publish site data to Active Directory Domain Services (AD DS)|When you publish site data to AD DS, you make it easy for clients to find services and make efficient use of site resources.<br /><br /> You must first [Extend the Active Directory schema for System Center Configuration Manager](../System Center Configuration Manager/Extend-the-Active-Directory-schema-for-System-Center-Configuration-Manager.md), and then each site must be configured to [Publish site data for System Center Configuration Manager](../System Center Configuration Manager/Publish-site-data-for-System-Center-Configuration-Manager.md) individually.|  
|Configure a service connection point|At the top-tier site of your hierarchy you should plan to install and configure the service connection point. For information, see [About the service connection point in System Center Configuration Manager](../System Center Configuration Manager/About-the-service-connection-point-in-System-Center-Configuration-Manager.md).|  
|Add site system roles|Install one or more additional site system roles to individual sites.  See [Add site system roles for System Center Configuration Manager](../System Center Configuration Manager/Add-site-system-roles-for-System-Center-Configuration-Manager.md)|  
|Configure site boundaries and boundary groups|Specify boundaries that define network locations on your intranet that can contain devices that you want to manage, and then configure boundary groups so that clients at those network locations can find [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] services resources. See [Define site boundaries and boundary groups for System Center Configuration Manager](../System Center Configuration Manager/Define-site-boundaries-and-boundary-groups-for-System-Center-Configuration-Manager.md)|  
|Configure distribution point groups|Configure logical  groups of distribution points to make managing deployments easier. See [Manage distribution point groups](../System Center Configuration Manager/Install-and-configure-distribution-points-for-System-Center-Configuration-Manager.md#bkmk_manage) in [Install and configure distribution points for System Center Configuration Manager](../System Center Configuration Manager/Install-and-configure-distribution-points-for-System-Center-Configuration-Manager.md).|  
|Run Discovery|Run discovery to find resources on your network including network infrastructure, devices, and users.<br /><br /> See [Run discovery for System Center Configuration Manager](../System Center Configuration Manager/Run-discovery-for-System-Center-Configuration-Manager.md)|  
|Add redundancy and capacity for those who manage your infrastructure|You can install additional SMS Providers and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles to expand capacity for administrators to manage your infrastructure:<br /><br /> **Install additional SMS Providers** to provide redundancy for contact points to administer your site and hierarchy. See [Manage the SMS Provider](../System Center Configuration Manager/Modify-your-System-Center-Configuration-Manager-infrastructure.md#BKMK_ManageSMSprovider) in [Modify your System Center Configuration Manager infrastructure](../System Center Configuration Manager/Modify-your-System-Center-Configuration-Manager-infrastructure.md)<br /><br /> **Install additional Configuration Manager consoles** to provide access to additional administrative users at the same time. See [Install Configuration Manager consoles](../System Center Configuration Manager/Install-System-Center-Configuration-Manager-consoles.md)|  
|Configure site components|You can configure site components at each site to modify the behavior of site system roles and site status reporting. See [Site components for System Center Configuration Manager](../System Center Configuration Manager/Site-components-for-System-Center-Configuration-Manager.md)|  
|Create custom collections|Using information that is discovered about devices and users, create custom collections of objects to simplify future management tasks. See [How to create collections in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-collections-in-System-Center-Configuration-Manager.md)|  
|Configure settings to manage high-risk deployments|Configure settings at a site that will warn administrative users when they create a high-risk task sequence deployment.  See [Settings to manage high-risk deployments for System Center Configuration Manager](../System Center Configuration Manager/Settings-to-manage-high-risk-deployments-for-System-Center-Configuration-Manager.md)|  
|Configure database replicas for management points|Configure a database replica to reduce the CPU load placed on the site database server by management points as they service requests from clients. See [Database replicas for management points for System Center Configuration Manager](../System Center Configuration Manager/Database-replicas-for-management-points-for-System-Center-Configuration-Manager.md)|  
|Configure a SQL Server AlwaysOn Availability Group to host the site database|Beginning with version 1602, you can configure availability groups as a high-availability and disaster-recovery solution for hosting the site database at primary sites and the central administration site. See [SQL Server AlwaysOn for a highly available site database for System Center Configuration Manager](../System Center Configuration Manager/SQL-Server-AlwaysOn-for-a-highly-available-site-database-for-System-Center-Configuration-Manager.md)|  
|Modify replication between sites|See [Data transfers between sites in System Center Configuration Manager](../System Center Configuration Manager/Data-transfers-between-sites-in-System-Center-Configuration-Manager.md) to learn about the following subjects:<br /><br /> Configure [File-based replication](../System Center Configuration Manager/Data-transfers-between-sites-in-System-Center-Configuration-Manager.md#bkmk_fileroute) between secondary sites<br /><br /> Configure [Database replication links](../System Center Configuration Manager/Data-transfers-between-sites-in-System-Center-Configuration-Manager.md#bkmk_Dblinks)<br /><br /> Configure [Distributed views](../System Center Configuration Manager/Data-transfers-between-sites-in-System-Center-Configuration-Manager.md#bkmk_distviews)|  
  
## See Also  
 [Start using System Center Configuration Manager](../System Center Configuration Manager/Start-using-System-Center-Configuration-Manager.md)