---
title: "Planning to monitor migration activity in System Center Configuration Manager"
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
ms.assetid: fc731d3f-edd7-4049-b17b-653d6693a564
caps.latest.revision: 4
caps.handback.revision: 0
---
# Planning to monitor migration activity in System Center Configuration Manager
With [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you can monitor migration in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console that connects to the destination hierarchy. In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console in the **Administration** workspace, you can use the **Migration** node to monitor the progress and success of migration jobs. You can view summary information for each migration job that identifies objects that have migrated, those objects that have not yet migrated, and the number of objects that are excluded from a migration job. You will also see details about any migration problems.  
  
## View Migration Progress  
 To view the progress of a migration job, use any of the following actions:  
  
-   In the **Administration** workspace of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, expand the **Migration Jobs** node, select a migration job, and then select the **Objects in Job** tab.  
  
-   Use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] log files to review the migration progress or to identify any problems. Migration Manager is the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] process that tracks migration actions and records these in the migmctrl.log file in the **\<InstallationPath\>\\LOGS** folder on the site server.  
  
    > [!NOTE]  
    >  If a migration job fails, review the details in the migmctrl.log file as soon as possible. The migration log entries are continually added to the file and overwrite old details. If the entries are overwritten, you might not be able to identify whether any problems that you might encounter with the migrated objects relate to migration issues. Migration activity is logged at the top\-level site of the hierarchy regardless of the site your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console connects to when you configure migration.  
  
-   Use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reporting. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides several built\-in reports for migration, or you can edit those reports to fit your requirements. For more information about [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Planning for migration to System Center Configuration Manager](../System Center Configuration Manager/Planning-for-migration-to-System-Center-Configuration-Manager.md)