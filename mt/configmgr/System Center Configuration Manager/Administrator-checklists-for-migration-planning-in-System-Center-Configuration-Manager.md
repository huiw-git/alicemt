---
title: "Administrator checklists for migration planning in System Center Configuration Manager"
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
ms.assetid: 295fdf07-93cc-490c-acdd-ce3ee88cb36f
caps.latest.revision: 7
caps.handback.revision: 0
---
# Administrator checklists for migration planning in System Center Configuration Manager
Use the following administrator checklists to help you plan your migration strategy to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:  
  
-   [Administrator checklist for migration planning](#Checklist_Migraiton_Planning)  
  
-   [Administrator checklist for hierarchy migration](#Checklist_Hierarchy_for_migration)  
  
-   [Administrator checklist for migration](#Checklisit_Migration)  
  
##  <a name="Checklist_Migraiton_Planning"></a> Administrator checklist for migration planning  
 Use the following checklist for pre-migration planning steps.  
  
-   **Assess the current environment:**  
  
     Identify existing business requirements that are met by the source hierarchy and develop plans to continue to meet those requirements in the destination hierarchy.  
  
-   **Review the functionality and changes that are available with the version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] that you use, and use this information to help you design your destination hierarchy:**  
  
     For more information, see [Fundamentals of System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-System-Center-Configuration-Manager.md) and [What's new in System Center Configuration Manager](../Topic/What's%20new%20in%20System%20Center%20Configuration%20Manager.md).  
  
-   **Determine the administrative security model to use for role-based administration:**  
  
     For more information, see [Fundamentals of role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-role-based-administration-for-System-Center-Configuration-Manager.md).  
  
-   **Assess your network and Active Directory topology:**  
  
     Review your existing domain structure and network topology and consider how this influences your hierarchy design and migration tasks.  
  
-   **Finalize your destination hierarchy design:**  
  
     Decide upon the placement of a central administration site, primary sites, secondary sites, and content distribution options.  
  
-   **Map your hierarchy to the computers that you will use for sites and site servers in the destination hierarchy:**  
  
     Identify the computers that sites and site system servers will use in the destination hierarchy, and ensure that they have sufficient capacity to meet existing and future operational requirements.  
  
-   **Plan your object migration strategy:**  
  
     Plan to use the available migration jobs to migrate different objects, which include site boundaries, collections, advertisements, and deployments. For more information, see [Types of Migration Jobs](../System Center Configuration Manager/Planning-a-migration-job-strategy-in-System-Center-Configuration-Manager.md#Types_of_Migration) in [Planning a migration job strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-migration-job-strategy-in-System-Center-Configuration-Manager.md)  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] migrates only the objects that you select. Any objects that are not migrated and that are required in the destination hierarchy must be re-created in the destination hierarchy.  
  
     Objects that can migrate are displayed when you configure migration jobs.  
  
-   **Plan your client migration strategy:**  
  
     Plan to migrate clients by using a controlled approach that limits the network bandwidth and server processing requirements when you migrate clients to the destination hierarchy. For more information about planning a client migration strategy, see [Planning a client migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-client-migration-strategy-in-System-Center-Configuration-Manager.md).  
  
-   **Plan for inventory and compliance data:**  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support migrating hardware inventory, software inventory, or desired configuration management compliance data for software updates or clients.  
  
     Instead, after the client migrates to its new site in the destination hierarchy and receives policy for these configurations, the client submits this information to its assigned site. This action populates the destination site database with current inventory and compliance data.  
  
-   **Plan for the completion of migration from the source hierarchy:**  
  
     Decide when objects and clients will be migrated. After migration completes, you can plan to decommission the site servers in the source hierarchy.  
  
##  <a name="Checklist_Hierarchy_for_migration"></a> Administrator checklist for hierarchy migration  
 Use the following checklist to help you plan a destination hierarchy before you start migration.  
  
-   **Identify the computers to use in the destination hierarchy:**  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support an in-place upgrade from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 infrastructure. Instead you use migration to move data from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. This requires you to use a side-by-side deployment and install [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] on new computers.  
  
     Similarly, when you migrate from another [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy, you must install a new destination hierarchy that is a side-by-side deployment to your source hierarchy.  
  
-   **Create your destination hierarchy:**  
  
     To prepare for migration, install and configure a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] destination hierarchy that includes a primary site. For example:  
  
    -   Install a central administration site and then install at least one child primary  
  
    -   Install a stand-alone primary if you do not plan to use a central administration site.  
  
-   **If you want to migrate information that is related to software updates, configure a software update point in the destination hierarchy and synchronize software updates:**  
  
     You must configure and synchronize software updates in the destination hierarchy before you can migrate software updates information from the source hierarchy.  
  
     For more information, see [Configure software updates in System Center Configuration Manager](../System Center Configuration Manager/Configure-software-updates-in-System-Center-Configuration-Manager.md).  
  
-   **Install and configure additional site system roles in the destination hierarchy:**  
  
     Configure additional site system roles and site systems that you will require.  
  
-   **Verify operational functionality in the destination hierarchy:**  
  
     Check the following:  
  
    -   If the destination hierarchy includes multiple sites, confirm that database replication is working between sites. Database replication is not applicable to stand-alone primary sites.  
  
    -   Verify that all installed site system roles are operational.  
  
    -   Verify that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients you install to the destination hierarchy can communicate successfully with their assigned site.  
  
> [!NOTE]  
>  For more information about how to plan a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy, see [Plan for System Center Configuration Manager infrastructure](../System Center Configuration Manager/Plan-for-System-Center-Configuration-Manager-infrastructure.md).  
  
##  <a name="Checklisit_Migration"></a> Administrator checklist for migration  
 Use the following checklist to migrate data from the source hierarchy to the destination hierarchy.  
  
-   **Enable migration in the destination hierarchy:**  
  
     Configure a source hierarchy by specifying the top-level site of the source hierarchy. For more information about specifying the source site, see [Planning a source hierarchy strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md).  
  
-   **When the source hierarchy runs [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 SP2, select and configure additional sites in the source hierarchy:**  
  
     For each additional site in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 SP2 source hierarchy that you want to collect data from, you must configure credentials for data gathering. When you configure each source site, the data gathering process begins immediately and continues throughout the migration period until you stop data gathering for that site. Data gathering ensures that you can migrate objects from the source hierarchy that are updated or new since a previous data gathering process.  
  
    > [!NOTE]  
    >  When the source hierarchy runs [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or later, you do not need to configure additional source sites.  
  
-   **Configure distribution point sharing:**  
  
     You can share distribution points between the two hierarchies to make content for objects that you migrate available to clients in the destination hierarchy. This ensures that the same content remains available for clients in both hierarchies and that you can maintain this content until you stop gathering data and complete the migration.  
  
     For information about shared distribution points, see the [Share Distribution Points Between Source and Destination Hierarchies](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md#About_Shared_DPs_in_Migration) section in the [Planning a content deployment migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md) topic.  
  
-   **Create and run migration jobs to migrate objects associated with the clients in the source hierarchy:**  
  
     Create migration jobs to migrate objects between hierarchies. The required configurations for each migration job can vary depending on what data the job migrates.  
  
     For example, when you migrate content, regardless of the migration job you use, you must assign a site in the destination hierarchy to own management of that content. The assigned site will access the original source file location for the content and is responsible for distributing that content to distribution points in the destination hierarchy.  
  
     For more information, see the [Create and Edit Migration Jobs for System Center Configuration Manager](../System Center Configuration Manager/Operations-for-migrating-to-System-Center-Configuration-Manager.md#Create_Edit_migration_Jobs) section in the [Operations for migrating to System Center Configuration Manager](../System Center Configuration Manager/Operations-for-migrating-to-System-Center-Configuration-Manager.md) topic.  
  
-   **Migrate clients to the destination hierarchy:**  
  
     The process of migrating clients depends on your migration scenario:  
  
    -   When you migrate clients that have a client version that is not the same as the destination hierarchy, the client software must upgrade. Upgrade requires the removal of the current [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, followed by the installation of the new client version that matches the destination site.  
  
    -   When you migrate clients that have a client version that matches the version of the destination hierarchy, the client does not upgrade or reinstall. Instead, the client reassigns to a primary site in the destination hierarchy.  
  
     When you migrate a client to the destination hierarchy, the client is associated with its data that you previously migrated to that destination hierarchy.  
  
     For more information, see [Planning a client migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-client-migration-strategy-in-System-Center-Configuration-Manager.md).  
  
-   **Upgrade or reassign shared distribution points:**  
  
     When you no longer have to support clients in your source hierarchy, you can upgrade shared distribution points from a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 source site, or reassign shared distribution points from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source site. When you upgrade or reassign a distribution point, the site system role transfers to a primary site in the destination hierarchy and the distribution point is removed from the source site in the source hierarchy. When you upgrade or reassign a shared distribution point the content remains on the distribution point computer and you do not have to redeploy the content to new distribution points in the destination hierarchy.  
  
     You can also upgrade a distribution point that is co-located on a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 secondary site server. This removes the secondary site and results in only a distribution point in the destination hierarchy.  
  
     For information about shared distribution points, see the [Share Distribution Points Between Source and Destination Hierarchies](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md#About_Shared_DPs_in_Migration) section in the [Planning a content deployment migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md) topic.  
  
-   **Complete migration:**  
  
     After you have migrated data and clients from all sites in the source hierarchy, and you have upgraded applicable distribution points, you can complete migration. To complete migration you stop gathering data for each source site in the source hierarchy. You can then remove migration information that you do not need and decommission your source hierarchy infrastructure. For more information, see [Planning to complete migration in System Center Configuration Manager](../System Center Configuration Manager/Planning-to-complete-migration-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Planning for migration to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-migration-to-System-Center-Configuration-Manager.md)