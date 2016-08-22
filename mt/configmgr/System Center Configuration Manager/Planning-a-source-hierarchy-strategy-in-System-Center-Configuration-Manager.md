---
title: "Planning a source hierarchy strategy in System Center Configuration Manager"
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
ms.assetid: 4800a800-66c8-4c35-aebe-e413a23790c1
caps.latest.revision: 6
caps.handback.revision: 0
---
# Planning a source hierarchy strategy in System Center Configuration Manager
Before you configure a migration job in your [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] environment, you must configure a source hierarchy and gather data from at least one source site in that hierarchy. Use the following sections to help you plan for configuring source hierarchies, configuring source sites, and determining the way in which [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] gathers information from the source sites in the source hierarchy.  
  
-   [Source hierarchies](#BKMK_Source_Hierarchies)  
  
-   [Source sites](#BKMK_Source_Sites)  
  
-   [Data gathering](#BKMK_Data_Gathering)  
  
##  <a name="BKMK_Source_Hierarchies"></a> Source hierarchies  
 A source hierarchy is a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy that contains data that you want to migrate. When you configure migration and specify a source hierarchy, you specify the top-level site of the source hierarchy. This site is also called a source site. Additional sites that you can migrate data from in the source hierarchy are also called source sites:  
  
-   When you configure a migration job to migrate data from a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 source hierarchy, you configure it to migrate data from one or more specific source sites in the source hierarchy.  
  
-   When you configure a migration job to migrate data from a source hierarchy that runs [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or later, you only need to specify the top-level site.  
  
 You can configure only one source hierarchy at a time:  
  
-   If you configure a new source hierarchy, that hierarchy automatically becomes the current source hierarchy replacing the previous source hierarchy.  
  
-   When you configure a source hierarchy you must specify the top-level site of the source hierarchy specify credentials for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to use to connect to the SMS Provider and site database of that source site.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses these credentials to run data gathering to retrieve information about the objects and distribution points from the source site.  
  
-   As part of the data gathering process, child sites in the source hierarchy are identified.  
  
-   If the source hierarchy is a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 hierarchy, you can then configure those additional sites as source sites, with separate credentials for each source site.  
  
 Although you can configure multiple source hierarchies in succession, migration is active for only one source hierarchy at a time:  
  
-   If you configure an additional source hierarchy before you complete migration from the current source hierarchy, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cancels any active migration jobs and postpones any scheduled migration jobs for the current source hierarchy.  
  
-   The newly configured source hierarchy then becomes the current source hierarchy and the original source hierarchy is now inactive.  
  
-   You can then configure connection credentials, additional source sites, and migration jobs for the new source hierarchy.  
  
 If you restore an inactive source hierarchy, and you have not previously used the **Cleanup Migration Data** action, you can view the previously configured migration jobs for that source hierarchy. However, before you can continue migration from that hierarchy, you must reconfigure the credentials to connect to applicable source sites in the hierarchy, and then reschedule any migration jobs that did not finish.  
  
> [!CAUTION]  
>  If you migrate data from more than a single source hierarchy, each additional source hierarchy must contain a unique set of site codes.  
  
 For more information about configuring a source hierarchy, see [Configuring source hierarchies and source sites for migration to System Center Configuration Manager](../System Center Configuration Manager/Configuring-source-hierarchies-and-source-sites-for-migration-to-System-Center-Configuration-Manager.md)  
  
##  <a name="BKMK_Source_Sites"></a> Source sites  
 Source sites are the sites in the source hierarchy that have the data that you want to migrate. The top-level site of the source hierarchy is always the first source site. When migration collects data from the first source site of a new source hierarchy, it discovers information about additional sites in that hierarchy.  
  
 After data gathering completes for the initial source site, the actions you take next depend on the product version of the source hierarchy.  
  
### Source sites that run Configuration Manager 2007 SP2  
 After data is gathered from the initial source site of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 SP2 hierarchy, you do not have to configure additional source sites before you create migration jobs. However, before you can migrate data from additional sites, you must configure additional sites as source sites, and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] must successfully gather data from those sites.  
  
 To gather data from additional sites, you individually configure each site as a source site. This requires you to specify the credentials for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to connect to the SMS Provider and site database of each source site. After you configure the credentials for a source site, the data gathering process for that site begins.  
  
 When you configure additional source sites in a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 SP2 source hierarchy, you must configure source sites from the top down, which means you configure the bottom-tier sites last. You can configure source sites in a branch of the hierarchy at any time, but you must configure a site as a source site before you configure any of its child sites as source sites.  
  
> [!NOTE]  
>  Only primary sites in a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 SP2 hierarchy are supported for migration.  
  
### Source sites that run System Center 2012 Configuration or later  
 After data is gathered from the initial source site of the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or later hierarchy, you do not have to configure additional source sites in that source hierarchy. This is because unlike [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007, these versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] use a shared database and the shared database allows you to identify and then migrate all available objects from the initial source site.  
  
 However, when you configure the access accounts to gather data, you might need to grant the **Source Site SMS Provider Account** access to multiple computers in the source hierarchy. This might be needed when the source site supports multiple instances of the SMS Provider, each on a different computer. When data gathering begins, the top-level site of the destination hierarchy contacts the top-level site in the source hierarchy to identify the locations of the SMS Provider for that site. Only the first instance of the SMS provider is identified. If the data gathering process cannot access the SMS Provider at the location it identifies, the process fails and does not try to connect to additional computers that run an instance of SMS Provider for that site.  
  
##  <a name="BKMK_Data_Gathering"></a> Data gathering  
 Immediately after you specify a source hierarchy, configure credentials for each additional source site in a source hierarchy, or share the distribution points for a source site, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] starts to gather data from the source site.  
  
 The data gathering process then repeats itself on a simple schedule to maintain synchronization with any changes to data in the source site. By default, the process repeats every four hours. You can modify the schedule for this cycle by editing the **Properties** of the source site. The initial data gathering process must review all objects in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database and can take time to finish. Subsequent data gathering processes identify only changes to the data and require less time to finish.  
  
 To gather data, the top-level site in the destination hierarchy connects to the SMS Provider and the site database of the source site to retrieve a list of objects and distribution points. These connections use the source site access accounts. For information about required configurations for gathering data, see [Prerequisites for migration in System Center Configuration Manager](../System Center Configuration Manager/Prerequisites-for-migration-in-System-Center-Configuration-Manager.md).  
  
 You can start and stop the data gathering process by using the **Gather Data Now**, and **Stop Gathering Data** actions in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
 After you use the **Stop Gathering Data** option for a source site for any reason, you must reconfigure credentials for the site before you can gather data from that site again. Until you reconfigure the source site, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot identify new objects or changes to previously migrated objects at that site.  
  
> [!NOTE]  
>  Before you expand a stand-alone primary site into a hierarchy with a central administration site, you must stop all Data Gathering. You can reconfigure Data Gathering after the site expansion completes.  
  
### Gather Data Now  
 After the initial data gathering process runs for a site, this process repeats itself to identify objects that have updated since the last data gathering cycle. You can also use the **Gather Data Now** action in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to immediately start the process and to reset the start time of the next cycle.  
  
 After a data gathering process successfully finishes for a source site, you can share the distribution points from the source site and configure migration jobs to migrate data from the site. Data gathering is a repeating process for migration and continues until you change the source hierarchy, or use the **Stop Gathering Data** action to end the data gathering process for that site.  
  
### Stop Gathering Data  
 You can use the **Stop Gathering Data** action to end the data gathering process for a source site when you no longer want [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to identify new or changed objects from that site. This action also prevents [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] from offering clients in the destination hierarchy any shared distribution points from the source as content locations for the content that you have migrated.  
  
 To stop gathering data from each source site, you must perform the **Stop Gathering Data** action on the bottom-tier source sites, and then repeat the process at each parent site. The top-level site of the source hierarchy must be the last site on which you stop gathering data. You must stop data gathering at each child site before performing this action at a parent site. Typically, you only stop gathering data when you are ready to complete the migration process.  
  
 After you stop gathering data for a source site, information previously gathered about object and collections from that site remain available to use when you configure new migration jobs. However, you do not see any new objects or collections, or see changes that were made to existing objects. If you reconfigure the source site and begin gathering data again, you will see information and status about previously migrated objects.  
  
## See Also  
 [Planning for migration to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-migration-to-System-Center-Configuration-Manager.md)