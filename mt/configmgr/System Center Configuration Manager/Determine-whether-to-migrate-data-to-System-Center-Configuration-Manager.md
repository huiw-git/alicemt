---
title: "Determine whether to migrate data to System Center Configuration Manager"
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
ms.assetid: 99222dc8-0e1e-4513-8302-7a1acf671e9b
caps.latest.revision: 6
caps.handback.revision: 0
---
# Determine whether to migrate data to System Center Configuration Manager
In [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] migration provides a process to  transfer data and configurations you have made from supported versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to your new hierarchy.  You can use this to:  
  
-   Combine multiple hierarchies into one  
  
-   Move data and configurations from a lab deployment into your production deployment  
  
-   Move data and configuration from a prior version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], like [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 which has no upgrade path to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], or from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] (which does support an upgrade path to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]).  
  
 With the exception of the distribution point site system role and the computers that host distribution points, no infrastructure (which includes sites, site system roles, or computers that host a site system role), migrates, transfers, or can be shared between hierarchies.  
  
 Although you cannot migrate server infrastructure, you can migrate [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients between hierarchies. Client migration involves migrating the data that clients use from the source hierarchy to the destination hierarchy, and then installing or reassigning the client software so that the client then reports to the new hierarchy. After you install a client to the new hierarchy and the client submits its data, its unique [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] ID helps [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] associate that data that you previously migrated with each client computer.  
  
 The functionality provided by migration helps you maintain investments that you have made in configurations and deployments while you can take full advantage of core changes in the product first introduced in [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and continued in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. These changes include a simplified [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy that uses fewer sites and resources, and the improved processing by using native 64-bit code that runs on 64-bit hardware.  
  
 For information about the versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] that migration supports, see [Prerequisites for migration in System Center Configuration Manager](../System Center Configuration Manager/Prerequisites-for-migration-in-System-Center-Configuration-Manager.md).  
  
 The following sections can help you plan for data that you can or cannot migrate:  
  
-   [Data that you can migrate to System Center Configuration Manager](#Can_Migrate)  
  
-   [Data that you cannot migrate to System Center Configuration Manager](#Cannot_migrate)  
  
##  <a name="Can_Migrate"></a> Data that you can migrate to System Center Configuration Manager  
 Migration can migrate most objects from between supported [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchies. The migrated instances of some objects from a supported version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 must be modified to conform to the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] schema and object format. These modifications do not affect the data in the source site database. Objects migrated from a supported version of [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] do not require modification.  
  
 The following are objects that can migrate based on the version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in the source hierarchy. Some objects, like queries, do not migrate. If you want to continue to use these objects that do not migrate you must recreate them in the new hierarchy. Other objects, which includes some client data, are automatically recreated in the new hierarchy when you manage clients in that hierarchy.  
  
 **Objects you can migrate from System Center 2012 Configuration Manager or System Center Configuration Manager current branch:**  
  
-   Advertisements  
  
-   Applications for [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and later versions  
  
-   App-V Virtual Environment from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and later versions  
  
-   Asset Intelligence customizations  
  
-   Boundaries  
  
-   Collections - To migrate collections from a supported version of System Center 2012 Configuration Manager or System Center Configuration Manager, you use an object migration job.  
  
-   Compliance settings:  
  
    -   Configuration baselines  
  
    -   Configuration items  
  
-   Operating system deployment:  
  
    -   Boot images  
  
    -   Driver packages  
  
    -   Drivers  
  
    -   Images  
  
    -   Packages  
  
    -   Task sequences  
  
-   Search results - Saved search criteria  
  
-   Software updates:  
  
    -   Deployments  
  
    -   Deployment packages  
  
    -   Templates  
  
    -   Software update lists  
  
-   Software distribution packages  
  
-   Software metering rules  
  
-   Virtual application packages  
  
 **Objects you can migrate from Configuration Manager 2007 SP2:**  
  
-   Advertisements  
  
-   Applications for [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and later versions  
  
-   App-V Virtual Environment from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and later versions  
  
-   Asset Intelligence customizations  
  
-   Boundaries  
  
-   Collections - You migrate collections from a supported version of Configuration Manager 2007 by using a collection migration job.  
  
-   Compliance settings (referred to as desired configuration management in Configuration Manager 2007):  
  
    -   Configuration baselines  
  
    -   Configuration items  
  
-   Operating system deployment:  
  
    -   Boot images  
  
    -   Driver packages  
  
    -   Drivers  
  
    -   Images  
  
    -   Packages  
  
    -   Task sequences  
  
-   Search results - Search folders  
  
-   Software updates:  
  
    -   Deployments  
  
    -   Deployment packages  
  
    -   Templates  
  
    -   Software update lists  
  
-   Software distribution packages  
  
-   Software metering rules  
  
-   Virtual application packages  
  
##  <a name="Cannot_migrate"></a> Data that you cannot migrate to System Center Configuration Manager  
 You cannot migrate the following types of objects:  
  
-   AMT client provisioning information  
  
-   Files on clients, which includes:  
  
    -   Client inventory and history data  
  
    -   Files in the client cache  
  
-   Queries  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 security rights and instances for the site and objects  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 reports from SQL Server Reporting Services  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 web reports  
  
-   [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] reports  
  
-   [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] role-based administration:  
  
    -   Security roles  
  
    -   Security scopes  
  
## See Also  
 [Planning for migration to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-migration-to-System-Center-Configuration-Manager.md)