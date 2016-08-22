---
title: "Fundamentals of sites and hierarchies for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-04-18
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 4db1e15f-e832-4cf9-be33-d3971e635a55
caps.latest.revision: 6
---
# Fundamentals of sites and hierarchies for System Center Configuration Manager
A [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] deployment must be installed in an Active Directory domain and has a foundation of one or more Configuration Manager sites that form a hierarchy of sites. From a single site to a multi-site hierarchy, the type and location of sites you install provide the ability to scale up (expand) your deployment when necessary, and deliver key services to managed users and devices. 

## Hierarchies of sites
When you install [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] for the first time, the first [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that you install determines the scope of your hierarchy - the foundation from which you will manage devices and users in your enterprise. This first site must be either a central administration site, or a stand-alone primary site.  
  
 A **central administration site** is suitable for large-scale deployments,  provides a central point of administration, and the flexibility to support devices that are distributed across a global network infrastructure. After you install a  central administration site you will need to install one or more primary sites as child sites.  This is because a central administration site does not directly support management of devices, which is the function of a primary site. A central administration site supports multiple child primary sites which you use to directly manage devices and to control network bandwidth when your managed devices are in different geographical locations.  
  
 A **stand-alone primary site** is suitable for smaller deployments, and can be used to manage devices without having to install additional sites. While a stand-alone primary site can limit the size of your deployment, it does support a scenario to expand your hierarchy at a later time by installing a new central administration site. With this site expansion scenario your stand-alone primary site becomes a child-primary site and you can then install additional child-primary sites below your new central administration site.  This then enables you to expand your initial deployment for future growth of your enterprise.  
  
> [!TIP]  
>  A stand-alone primary site and a child-primary site are really the same type of site: a primary site. The difference in name is based on the hierarchy relationship that is created when you also use a central administration site.  This hierarchy relationship can also limit the installation of certain site system roles that extend [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] functionality. This is because certain site system roles can only be installed on the top-tier site of the hierarchy, a central administration site or stand-alone primary site.  
  
 After you install your first site, you can install additional sites.  If your first site was a central administration site, then you can install one or more child-primary sites.  After you install a primary site (stand-alone, or child-primary) you can then install one or more secondary sites.  
  
 A **secondary site** can only be installed as a child site below a primary site. This site type extends the reach of a primary site to manage devices in locations that have a slow network connection to the primary site.   Even though a secondary site extends the primary site, clients are still managed by the primary site. The secondary site provides support for devices in the remote location by compressing and then managing the transfer of   information across your network that you send (deploy) to clients,  and that clients send back to the site.  
  
 The following diagrams show some example site designs.  
  
 ![Hierarchy&#95;examples](../System Center Configuration Manager/medias/Hierarchy_examples.png "Hierarchy_examples")  
  
 For more information, see the following topics:  
  
-   [Introduction to System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-System-Center-Configuration-Manager.md)  
  
-   [Design a hierarchy of sites for System Center Configuration Manager](../System Center Configuration Manager/Design-a-hierarchy-of-sites-for-System-Center-Configuration-Manager.md)  
  
-   [Install System Center Configuration Manager sites](../Topic/Install%20System%20Center%20Configuration%20Manager%20sites.md)  
  
## Site system servers and site system roles  
 Each [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site installs **site system roles** that support  management operations.  Some roles are installed by default when you install a site, like the **site  server** role (which is assigned to the computer where you install the site), and site database server role (which is assigned to the SQL Server that hosts the site database). Other site system roles are optional and only used when you want to use the functionality that a site system role enables.  Any computer that hosts a site system role is referred to as a site system server.  
  
 For a smaller deployment of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] you might initially run all of your site system roles directly on the site server computer. Then, as your managed environment and needs grow, you can  install additional site system servers to host additional site system roles to improve the sites efficiency in providing services to more devices.  
  
 For information about the different site system roles, see [Site system roles](../System Center Configuration Manager/Plan-for-site-system-servers-and-site-system-roles-for-System-Center-Configuration-Manager.md#bkmk_planroles) in [Plan for site system servers and site system roles for System Center Configuration Manager](../System Center Configuration Manager/Plan-for-site-system-servers-and-site-system-roles-for-System-Center-Configuration-Manager.md)  
  
## Publishing site information to Active Directory Domain Services  
 To simplify management of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can extend the Active Directory schema to support details used by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)],  and then have sites publish their key information to Active Directory Domain Services (AD DS). This enables the computers that you want to manage to securely retrieve site related  information from the trusted source of AD DS. The information clients can retrieve identifies available sites, site system servers, and the services that those site system servers provide.  
  
 **Extending the Active Directory schema** is done only one time per forest and can be done before or after you install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].   When you  extend the schema, you must create a new Active Directory container named **System Management** in each domain that contains a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that will publish data for clients to find. For more information, see [Extend the Active Directory schema for System Center Configuration Manager](../System Center Configuration Manager/Extend-the-Active-Directory-schema-for-System-Center-Configuration-Manager.md).  
  
 **Publishing site data** improves the security of your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy and reduces administrative overhead, but  is not required for basic [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] functionality.  
  
## See Also  
 [Fundamentals of System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-System-Center-Configuration-Manager.md)