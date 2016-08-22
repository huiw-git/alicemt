---
title: "Introduction to queries in System Center Configuration Manager"
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
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
caps.latest.revision: 5
caps.handback.revision: 0
---
# Introduction to queries in System Center Configuration Manager
You can create and run queries to locate objects in a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy that match your query criteria. These objects include items such as specific types of computers or user groups. Queries can return most types of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] objects, which include sites, collections, applications, and inventory data.  
  
 When you create a query, you must specify a minimum of two parameters: where you want to search and what you want to search for. For example, to find the amount of hard disk space that is available on all computers in a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, you can create a query to search the **Logical Disk** attribute class and the **Free Space (MB)** attribute for available hard disk space.  
  
 After you create an initial query, you can specify additional query criteria. For example, you can specify that the query results include only computers that are assigned to a specified site. You can also modify how results are displayed so that you can view the results in an order that is meaningful to you. For example, you can specify that the results are sorted by the amount of free hard disk space in either ascending or descending order.  
  
 When you create a query, it is stored by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and displayed in the **Queries** node in the **Monitoring** workspace. From this location, you can create a new query and then run, update, or manage an existing query.  
  
 You can also import a query into a query rule in a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collection. For more information, see [How to create collections in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-collections-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Queries technical reference for System Center Configuration Manager](../System Center Configuration Manager/Queries-technical-reference-for-System-Center-Configuration-Manager.md)