---
title: "Planning for the migration of Configuration Manager objects to System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 066caf00-e419-4efb-93d3-ba4ba878297c
caps.latest.revision: 7
caps.handback.revision: 0
---
# Planning for the migration of Configuration Manager objects to System Center Configuration Manager
With [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you can migrate many of the different objects that are associated with different features found at a source site. Use the following sections to help you plan for the migration of objects between hierarchies.  
  
-   [Planning to migrate software updates](#Plan_migrate_Software_updates)  
  
-   [Planning to migrate content](#Plan_Migrate_content)  
  
-   [Planning to migrate collections](#BKMK_MigrateCollections)  
  
-   [Planning to migrate operating system deployments](#Plan_migrate_OSD)  
  
-   [Planning to migrate desired configuration management](#Plan_Migrate_Compliance_settings)  
  
-   [Planning to migrate boundaries](#Plan_migrate_Boundaries)  
  
-   [Planning to migrate reports](#Plan_Migrate_reports)  
  
-   [Planning to migrate organizational and search folders](#Plan_Migrate_Org_Folders)  
  
-   [Planning to migrate Asset Intelligence customizations](#Plan_Migrate_AI)  
  
-   [Planning to migrate software metering rules customizations](#Plan_Migrate_SWM_Rules)  
  
##  <a name="Plan_migrate_Software_updates"></a> Planning to migrate software updates  
 You can migrate software update objects, such as software update packages and software update deployments.  
  
 To successfully migrate software update objects, you must first configure your destination hierarchy with configurations that match your source hierarchy environment. This requires the following actions:  
  
-   Deploy an active software update point in the destination hierarchy.  
  
-   Configure the catalog of products and languages to match the configuration of your source hierarchy.  
  
-   Synchronize the software update point in the destination hierarchy with a Windows Server Update Services (WSUS).  
  
 When you migrate software updates, consider the following:  
  
-   Migration of software update objects can fail when you have not synchronized information in your destination hierarchy to match the configuration of your source hierarchy.  
  
    > [!WARNING]  
    >  It is not supported to use the WSUSutil tool to synchronize data between a source and destination hierarchy.  
  
-   You cannot migrate custom updates that are published by using System Center Updates Publisher. Instead, custom updates must be republished to the destination hierarchy.  
  
 When you migrate from a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source hierarchy, the migration process modifies some software updates objects to the format in use by the destination hierarchy. Use the following table to help you plan the migration of software update objects from [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)].  
  
|[!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] object|Object name after migration|  
|-----------------------------------|---------------------------------|  
|Software update lists|Software update lists are converted to software update groups.|  
|Software update deployments|Software update deployments are converted to deployments and update groups.<br /><br /> After you migrate a software update deployment from [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)], you must enable it in the destination hierarchy before you can deploy it.|  
|Software update packages|Software update packages remain software update packages.|  
|Software update templates|Software update templates remain software update templates.<br /><br /> The **Duration** value in [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] deployment templates does not migrate.|  
  
 When you migrate objects from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchy, the software updates objects are not modified.  
  
##  <a name="Plan_Migrate_content"></a> Planning to migrate content  
 You can migrate content from a supported source hierarchy to your destination hierarchy. For a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source hierarchy, this content includes software distribution packages and programs and virtual applications, such as Microsoft Application Virtualization (App-V). For [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchies, this content includes applications, and App-V virtual applications. When you migrate content between hierarchies, it is the compressed source files that migrate to the destination hierarchy.  
  
### Packages and programs  
 When you migrate packages and programs, they are not modified by migration. However, before you migrate these, you must configure each package to use a Universal Naming Convention (UNC) path for its source file location. As part of the configuration to migrate packages and programs, you must assign a site in the destination hierarchy to manage this content. The content is not migrated from the assigned site, but after migration the assigned site accesses the original source file location by using the UNC mapping.  
  
 After you migrate a package and program to the destination hierarchy and while migration from the source hierarchy remains active, you can make the content available to clients in that hierarchy by using a shared distribution point. To use a shared distribution point, the content must remain accessible on the distribution point at the source site. For information about shared distribution points, see the [Share distribution points between source and destination hierarchies](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md#About_Shared_DPs_in_Migration) section in the [Planning a content deployment migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md) topic.  
  
 For content that has migrated, if the content version changes in either source hierarchy or the destination hierarchy, clients can no longer access the content from the shared distribution point in the destination hierarchy. In this scenario, you must re-migrate the content to restore a consistent version of the package between the source hierarchy and the destination hierarchy. This information synchronizes during the data gathering cycle.  
  
> [!TIP]  
>  For each package that you migrate, update the package in the destination hierarchy. This action can prevent issues with deploying the package to distribution points in the destination hierarchy. However, when you update a package on the distribution point in the destination hierarchy, clients in that hierarchy will no longer be able to acquire that package from a shared distribution point. To update a package in the destination hierarchy, in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, navigate to the Software Library, right click on the package, and then select **Update Distribution Points**. Do this action for each package that you migrated.  
  
> [!TIP]  
>  You can use Microsoft System Center [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Package Conversion Manager to convert packages and programs into [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] applications. Download Package Conversion Manager from the [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=212950) site. For more information, see [Configuration Manager Package Conversion Manager](http://go.microsoft.com/fwlink/p/?LinkId=247245).  
  
### Virtual applications  
 When you migrate App-V packages from a supported [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] site, the migration process converts them to applications in the destination hierarchy. Additionally, based on existing advertisements for the App-V package, the following deployment types are created in the destination hierarchy:  
  
-   If there are no advertisements, one deployment type is created that uses the default deployment type settings.  
  
-   If one advertisement exists, one deployment type is created that uses the same settings as the [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] advertisement.  
  
-   If multiple advertisements exist, a deployment type is created for each [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] advertisement, using the settings for that advertisement.  
  
> [!IMPORTANT]  
>  If you migrate a previously migrated [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] App-V , the migration fails because virtual application packages do not support the overwrite migration behavior. In this scenario, you must delete the migrated virtual application package from the destination hierarchy, and then create a new migration job to migrate the virtual application.  
  
> [!NOTE]  
>  After you migrate an App-V package, you can use the Update Content Wizard to change the source path for App-V deployment types. For information on how to update content for a deployment type, see the [How to manage deployment types](../System Center Configuration Manager/Management-tasks-for-System-Center-Configuration-Manager-applications.md#BKMK_DeplType) section in the [Management tasks for System Center Configuration Manager applications](../System Center Configuration Manager/Management-tasks-for-System-Center-Configuration-Manager-applications.md) topic.  
  
 When you migrate from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchy, in addition to App-V deployment types and applications, you can migrate objects for the e App-V virtual environment. For information about App-V environments, see [Deploying App-V virtual applications with System Center Configuration Manager](../System Center Configuration Manager/Deploying-App-V-virtual-applications-with-System-Center-Configuration-Manager.md).  
  
### Advertisements  
 You can migrate advertisements from a supported [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source site to the destination hierarchy by using collection-based migration. If you upgrade a client, it retains the history of previously run advertisements to prevent the client from rerunning migrated advertisements.  
  
> [!NOTE]  
>  You cannot migrate advertisements for virtual packages. This is an exception to the migration of advertisements.  
  
### Applications  
 You can migrate applications from a supported [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchy to a destination hierarchy. If you reassign a client from the source hierarchy to the destination hierarchy, the client retains the history of previously installed applications to prevent the client from rerunning a migrated application.  
  
##  <a name="BKMK_MigrateCollections"></a> Planning to migrate collections  
 You can migrate the criteria for collections from a supported [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchy. For this, you use an object-based migration job. When you migrate a collection, you migrate the rules for the collection and not information about the members of the collection or information or objects related to the members of the collection.  
  
 Migration of the collection object is not supported when you migrate from a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source hierarchy.  
  
##  <a name="Plan_migrate_OSD"></a> Planning to migrate operating system deployments  
 You can migrate the following operating system deployment objects from a supported source hierarchy:  
  
-   Operating system images and packages. The source path of boot images are updated to the default image location for the Windows Administrative Installation Kit (Windows AIK) on the destination site. The following are requirements and limitations to migrating operating system images and packages:  
  
    -   To successfully migrate image files, the computer account of the SMS Provider server for the destination hierarchies top-level site must have **Read** and **Write** permission to the image source files of the source sites Windows AIK location.  
  
    -   When you migrate an operating system installation package, ensure that the configuration of the package on the source site points to the folder that contains the WIM file, and not to the WIM file itself. If the installation package points to the WIM file, the migration of the installation package will fail.  
  
    -   When you migrate a boot image package from a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source site, the package ID of the package is not maintained in the destination site. The result of this is that clients in the destination hierarchy cannot use boot image packages that are available on shared distribution points.  
  
-   Task sequences. When you migrate a task sequence that contains a reference to a client installation package, that reference is replaced with a reference to the client installation package of the destination hierarchy.  
  
    > [!NOTE]  
    >  When you migrate a task sequence, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] might migrate objects that are not required in the destination hierarchy. These objects include boot images and [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] client installation packages.  
  
-   Drivers and driver packages.  
  
##  <a name="Plan_Migrate_Compliance_settings"></a> Planning to migrate desired configuration management  
 You can migrate configuration items and configuration baselines.  
  
> [!NOTE]  
>  Uninterpreted configuration items from [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source hierarchies are not supported for migration. You cannot migrate or import these configuration items to the destination hierarchy. For information about uninterpreted configuration items, see the “Uninterpreted Configuration Item” section in the [About Configuration Items in Desired Configuration Management](http://go.microsoft.com/fwlink/?LinkId=103846) topic in the [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] documentation library.  
  
 You can import [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] Configuration Packs. The import process automatically converts the Configuration Pack to be compatible with [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
##  <a name="Plan_migrate_Boundaries"></a> Planning to migrate boundaries  
 You can migrate boundaries between hierarchies. When you migrate boundaries from [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)], each boundary from the source site migrates at the same time and is added to a new boundary group that is created in the destination hierarchy. When you migrate boundaries from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy, each boundary you select is added to a new boundary group in the destination hierarchy.  
  
 Each automatically created boundary group is enabled for content location but not for site assignment. This prevents overlapping boundaries for site assignment between the source and destination hierarchies. When you migrate from a or [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source site, this helps prevent new [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] clients that install from incorrectly assigning to the destination hierarchy. By default,  [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] clients do not automatically assign to [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] sites.  
  
 During migration, if you share a distribution point with the destination hierarchy, any boundaries that are associated with that distribution automatically migrate to the destination hierarchy. In the destination hierarchy, migration creates a new read-only boundary group for each shared distribution point. If you change the boundaries for the distribution point in the source hierarchy, the boundary group in the destination hierarchy updates with these changes during the next data gathering cycle.  
  
##  <a name="Plan_Migrate_reports"></a> Planning to migrate reports  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support the migration of reports. Instead, use SQL Server Reporting Services Report Builder to export reports from the source hierarchy, and then import them to the destination hierarchy.  
  
> [!NOTE]  
>  Because there are schema changes for reports between [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], test each report that you import from a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] hierarchy to ensure that it functions as expected.  
  
 For more information about reporting, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
##  <a name="Plan_Migrate_Org_Folders"></a> Planning to migrate organizational and search folders  
 You can migrate organizational folders and search folders from a supported source hierarchy to a destination hierarchy. In addition, from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchy, you can migrate the criteria for a saved search to a destination hierarchy.  
  
 By default, the migration process maintains your search folder and administrative folder structures for objects and collections when you migrate. However, in the Create Migration Job Wizard, on the **Settings** page, you can configure a migration job to not migrate the organizational structure for objects by clearing the check box for this option. The organizational structures of collections are always maintained.  
  
 One exception to this is a search folder that contains virtual applications. When an App-V package is migrated, the App-V package is transformed into an application in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. After migration of the search folder, only the remaining packages are found, and the search folder cannot locate an App-V package because of this conversion to an application when the App-V package migrates.  
  
 When you migrate a saved search from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchy, you migrate the criteria for the search, and not the information about the search results. Migration of a saved search is not applicable from a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source site.  
  
##  <a name="Plan_Migrate_AI"></a> Planning to migrate Asset Intelligence customizations  
 You can migrate customizations for Asset Intelligence from a supported source hierarchy to a destination hierarchy. There are no significant changes to the structure of Asset Intelligence customizations between [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] does not support the migration of Asset Intelligence objects from a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] site that is using Asset Intelligence Service 2.0 (AIS 2.0).  
  
##  <a name="Plan_Migrate_SWM_Rules"></a> Planning to migrate software metering rules customizations  
 There are no significant changes to software metering between [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. You can migrate your software metering rules from a supported source hierarchy to a destination hierarchy.  
  
 By default, software metering rules that you migrate to a destination hierarchy are not associated with a specific site in the destination hierarchy and instead apply to all clients in the hierarchy. To apply a software metering rule to clients at a specific site, you must edit the metering rule after it migrates.  
  
## See Also  
 [Planning for migration to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-migration-to-System-Center-Configuration-Manager.md)