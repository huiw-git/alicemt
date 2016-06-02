---
title: Get the Fields for All Events
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
---
# Get the Fields for All Events
  Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:  
  
-   package\_name  
  
-   event\_name  
  
-   event\_field  
  
-   field\_type  
  
-   column\_type  
  
 You can use the preceding information when configuring event sessions that use the bucketing target. For more information, see [SQL Server Extended Events Targets](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Targets.md).  
  
## Before you Begin  
 Before you create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events session, it is useful to get information about the fields associated with events.  
  
## To get the fields for all events using Query Editor  
  
-   In Query Editor, issue the following statements.  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## See Also  
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](../Topic/sys.dm_xe_objects%20\(Transact-SQL\).md)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](../Topic/sys.dm_xe_packages%20\(Transact-SQL\).md)  
  
  