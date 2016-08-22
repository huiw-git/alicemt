---
title: "How to manage queries in System Center Configuration Manager"
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
ms.assetid: e562e2a0-8df8-4952-952f-e8c38461c612
caps.latest.revision: 6
caps.handback.revision: 0
---
# How to manage queries in System Center Configuration Manager
Use the information in this topic to help you manage queries in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
 For information about how to create queries, see [How to create queries in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-queries-in-System-Center-Configuration-Manager.md).  
  
## How to manage queries  
 In the **Monitoring** workspace, select **Queries**, select the query to manage, and then select a management task.  
  
 Use the following table for more information about the management tasks that might require some information before you select them.  
  
|Management task|Details|More information|  
|---------------------|-------------|----------------------|  
|**Run**|Runs the selected query and displays the results in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.|No additional information.|  
|**Install Client**|Opens the **Install Client Wizard** that lets you install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on computers returned by the selected query.<br /><br /> This option is not available for queries that return mobile devices, users, or user groups.|For more information about how to install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients by using client push, see [Manage computer clients with System Center Configuration Manager](../System Center Configuration Manager/Manage-computer-clients-with-System-Center-Configuration-Manager.md).|  
|**Export**|Opens the **Export Objects Wizard** that lets you export this query to a Managed Object Format (MOF) file that can then be imported at another site.|No additional information.|  
|**Move**|Opens the **Move Selected Items** dialog box where you can move the selected query to a folder that you previously created under the **Queries** node.|No additional information.|  
  
## See Also  
 [Operations and maintenance for queries in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-queries-in-System-Center-Configuration-Manager.md)