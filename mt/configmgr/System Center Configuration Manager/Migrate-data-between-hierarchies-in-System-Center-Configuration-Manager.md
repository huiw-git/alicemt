---
title: "Migrate data between hierarchies in System Center Configuration Manager"
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
ms.assetid: cf014eb0-f8c2-4d37-b8d7-368d63a10b89
caps.latest.revision: 11
caps.handback.revision: 0
---
# Migrate data between hierarchies in System Center Configuration Manager
Use migration to transfer data from a supported source hierarchy to your [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] destination hierarchy.   When you migrate data from a source hierarchy:  
  
-   You access data from the site databases that you identify in the source infrastructure and then transfer that data to your current environment  
  
-   Migration does not change the data in the source hierarchy, but instead discovers the data and stores a copy in the database of the destination hierarchy  
  
 Consider the following when you plan your migration strategy:  
  
-   You can migrate an existing [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] SP2 infrastructure to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
-   You can migrate some or all of the supported data from a source site.  
  
-   You can migrate the data from a single source site to several different sites in the destination hierarchy.  
  
-   You can move data from multiple source sites to a single site in the destination hierarchy.  
  
##  <a name="BKMK_MigrationConcepts"></a> Concepts for Migration  
 Use the following information about the concepts and terms you might encounter when you use migration.  
  
|Concept or term|More information|  
|---------------------|----------------------|  
|Source hierarchy|A hierarchy that runs a supported version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and contains data that you want to migrate. When you configure migration, you identify the source hierarchy when specifying the top-level site of a source hierarchy. After you specify a source hierarchy, the top-level site of the destination hierarchy gathers data from the database of the designated source site to identify the data that you can migrate.<br /><br /> For more information, see the [Source hierarchies](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md#BKMK_Source_Hierarchies) section in the [Planning a source hierarchy strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md) topic.|  
|Source sites|The sites in the source hierarchy that have data that you can migrate to your destination hierarchy.<br /><br /> For more information, see the [Source sites](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md#BKMK_Source_Sites) section in the [Planning a source hierarchy strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md) topic.|  
|Destination hierarchy|A [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy where migration runs to import data from a source hierarchy.|  
|Data gathering|The ongoing process of identifying the information in a source hierarchy that you can migrate to your destination hierarchy. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] checks the source hierarchy on a schedule to identify any changes to information in the source hierarchy that you previously migrated and that you might want to update in the destination hierarchy.<br /><br /> For more information, see the [Data gathering](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md#BKMK_Data_Gathering) section in the [Planning a source hierarchy strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md) topic.|  
|Migration jobs|The process of configuring the specific objects to migrate, and then managing the migration of those objects to the destination hierarchy.<br /><br /> For more information, see [Planning a migration job strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-migration-job-strategy-in-System-Center-Configuration-Manager.md)|  
|Client migration|The process of transferring information that clients use from the database of the source site to the database of the destination hierarchy. This migration of data is then followed by an upgrade of client software on devices to the  client software version from the destination hierarchy.<br /><br /> For more information, see [Planning a client migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-client-migration-strategy-in-System-Center-Configuration-Manager.md).|  
|Shared distribution points|The distribution points from the source hierarchy that are shared with the destination hierarchy during the migration period.<br /><br /> During the migration period, clients assigned to sites in the destination hierarchy can obtain content from shared distribution points.<br /><br /> For more information, see the [Share distribution points between source and destination hierarchies](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md#About_Shared_DPs_in_Migration) section in the [Planning a content deployment migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md) topic|  
|Monitoring migration|The process of monitoring migration activities. You monitor the migration progress and success from the **Migration** node in the **Administration** workspace.<br /><br /> For more information, see [Planning to monitor migration activity in System Center Configuration Manager](../System Center Configuration Manager/Planning-to-monitor-migration-activity-in-System-Center-Configuration-Manager.md).|  
|Stop gathering data|The process of stopping data gathering from source sites. When you no longer have data to migrate from a source hierarchy, or if you want to temporarily suspend migration-related activities, you can configure the destination hierarchy to stop gathering data from the source hierarchy.<br /><br /> For more information, see the [Data gathering](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md#BKMK_Data_Gathering) section in the [Planning a source hierarchy strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md) topic.|  
|Clean up migration data|The process of finishing migration from a source hierarchy by removing information about the migration from the destination hierarchies database.<br /><br /> For more information, see [Planning to complete migration in System Center Configuration Manager](../System Center Configuration Manager/Planning-to-complete-migration-in-System-Center-Configuration-Manager.md).|  
  
## Typical workflow for Migration  
  
1.  Specify a supported source hierarchy.  
  
2.  Configure data gathering. Data gathering enables [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to collect information about data that can migrate from the source hierarchy.  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically repeats the process to collect data on a simple schedule until you stop the data gathering process. By default, the data gathering process repeats every four hours so that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can identify changes to data in the source hierarchy that you might want to migrate. Data gathering is also necessary to share distribution points from the source hierarchy to the destination hierarchy.  
  
3.  Create migration jobs to migrate data between the source and destination hierarchy.  
  
4.  You can stop the data gathering process at any time by using the **Stop Gathering Data** command. When you stop data gathering, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] no longer identifies changes to data in the source hierarchy, and can no longer share distribution points between the source and destination hierarchies. Typically, you use this action when you no longer plan to migrate data or share distribution points from the source hierarchy.  
  
5.  Optionally, after data gathering has stopped at all sites for the source hierarchy, you can clean up the migration data by using the **Clean Up Migration Data** command. This command deletes the historical data about migration from a source hierarchy from the database of the destination hierarchy.  
  
 After you migrate data from a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] source hierarchy that you will no longer use to manage your environment, you can plan to decommission that source hierarchy and infrastructure.  
  
##  <a name="BKMK_MigrationScenarios"></a> Migration scenarios  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the following migration scenarios.  
  
> [!NOTE]  
>  The expansion of a hierarchy that contains a stand-alone site into a hierarchy that contains a central administration site is not categorized as a migration. For information about hierarchy expansion, see the [Expand a stand-alone primary site](../System Center Configuration Manager/Use-the-Setup-Wizard-to-install-System-Center-Configuration-Manager-sites.md#bkmk_expand) section in the [Use the Setup Wizard to intall sites](../System Center Configuration Manager/Use-the-Setup-Wizard-to-install-System-Center-Configuration-Manager-sites.md) topic.  
  
### Migration from Configuration Manager 2007 hierarchies  
 When you use migration to migrate data from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 you can maintain your investment in your existing site infrastructure and gain the following benefits:  
  
|Benefit|More information|  
|-------------|----------------------|  
|Site database improvements|The [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] database supports full Unicode.|  
|Database replication between sites|Replication in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] is based on Microsoft SQL Server. This improves the performance of site-to-site data transfer.|  
|User-centric management|Users are the focus of management tasks in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. For example, you can distribute software to a user even if you do not know the device name for that user. Additionally, [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] gives users much more control over what software is installed on their devices and when that software is installed.|  
|Hierarchy simplification|In [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], the  central administration site type and changes to the behavior of primary and secondary sites let you build a simpler site hierarchy that uses less network bandwidth and requires fewer servers.|  
|Role-based administration|This central security model in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] offers hierarchy-wide security and management that corresponds to your administrative and business requirements.|  
  
> [!NOTE]  
>  Because of design changes that were first introduced in [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)], you cannot upgrade [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] infrastructure to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. However, in place upgrade is supported from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
### Migration from Configuration Manager 2012 or another System Center Configuration Manager hierarchy  
 The process of migrating data from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy are the same. This includes migrating data from multiple source hierarchies into a single destination hierarchy, such as when your company acquires additional resources that are already managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. Additionally, you can migrate data from a test environment to your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] production environment. This allows you to maintain your investment in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] test environment.  
  
## Additional topics for migration:  
  
-   [Planning for migration to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-migration-to-System-Center-Configuration-Manager.md)  
  
-   [Configuring source hierarchies and source sites for migration to System Center Configuration Manager](../System Center Configuration Manager/Configuring-source-hierarchies-and-source-sites-for-migration-to-System-Center-Configuration-Manager.md)  
  
-   [Operations for migrating to System Center Configuration Manager](../System Center Configuration Manager/Operations-for-migrating-to-System-Center-Configuration-Manager.md)  
  
-   [Security and privacy for migration to System Center Configuration Manager](../System Center Configuration Manager/Security-and-privacy-for-migration-to-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Start using System Center Configuration Manager](../System Center Configuration Manager/Start-using-System-Center-Configuration-Manager.md)