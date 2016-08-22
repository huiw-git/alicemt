---
title: "Planning for migration to System Center Configuration Manager"
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
ms.assetid: b2bf493e-1e10-496f-a139-2646522703ed
caps.latest.revision: 7
caps.handback.revision: 0
---
# Planning for migration to System Center Configuration Manager
Before you migrate data to a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] destination hierarchy, make sure that you are familiar with sites and hierarchies in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For more information about sites and hierarchies, see [Fundamentals of System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-System-Center-Configuration-Manager.md).  
  
 You must first install a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy to be the destination hierarchy before you can migrate data from a supported source hierarchy.  
  
 After you install the destination hierarchy, configure the management features and functions that you want to use in your destination hierarchy before you start to migrate data.  
  
 Additionally, you might have to plan for overlap between the source hierarchy and your destination hierarchy. As an example, consider when the source hierarchy is configured to use the same network locations or boundaries as your destination hierarchy and you then install new clients to your destination hierarchy and use automatic site assignment. In this scenario, because a newly installed [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client can select a site to join from either hierarchy, the client could incorrectly assign to your source hierarchy. Therefore, plan to assign each new client in the destination hierarchy to a specific site in that hierarchy instead of using automatic-site assignment.  
  
 For more information about site assignments, see the [Client site assignment considerations](../System Center Configuration Manager/Interoperability-between-different-versions-of-System-Center-Configuration-Manager.md#BKMK_SupConfigSiteAssignment) section in the [Interoperability between different versions of System Center Configuration Manager](../System Center Configuration Manager/Interoperability-between-different-versions-of-System-Center-Configuration-Manager.md) topic.  
  
## Planning Topics  
 Use the following topics to help you plan how to migrate a supported source hierarchy to a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] destination hierarchy:  
  
-   [Prerequisites for migration in System Center Configuration Manager](../System Center Configuration Manager/Prerequisites-for-migration-in-System-Center-Configuration-Manager.md)  
  
-   [Administrator checklists for migration planning in System Center Configuration Manager](../System Center Configuration Manager/Administrator-checklists-for-migration-planning-in-System-Center-Configuration-Manager.md)  
  
-   [Determine whether to migrate data to System Center Configuration Manager](../System Center Configuration Manager/Determine-whether-to-migrate-data-to-System-Center-Configuration-Manager.md)  
  
-   [Planning a source hierarchy strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-source-hierarchy-strategy-in-System-Center-Configuration-Manager.md)  
  
-   [Administrator checklists for migration planning in System Center Configuration Manager](../System Center Configuration Manager/Administrator-checklists-for-migration-planning-in-System-Center-Configuration-Manager.md)  
  
-   [Planning a client migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-client-migration-strategy-in-System-Center-Configuration-Manager.md)  
  
-   [Planning a content deployment migration strategy in System Center Configuration Manager](../System Center Configuration Manager/Planning-a-content-deployment-migration-strategy-in-System-Center-Configuration-Manager.md)  
  
-   [Planning for the migration of Configuration Manager objects to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-the-migration-of-Configuration-Manager-objects-to-System-Center-Configuration-Manager.md)  
  
-   [Planning to monitor migration activity in System Center Configuration Manager](../System Center Configuration Manager/Planning-to-monitor-migration-activity-in-System-Center-Configuration-Manager.md)  
  
-   [Planning to complete migration in System Center Configuration Manager](../System Center Configuration Manager/Planning-to-complete-migration-in-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Migrate data between hierarchies in System Center Configuration Manager](../System Center Configuration Manager/Migrate-data-between-hierarchies-in-System-Center-Configuration-Manager.md)