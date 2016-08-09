---
title: "Get the Fields for All Events"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# Get the Fields for All Events
Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
 After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:  
  
-   package_name  
  
-   event_name  
  
-   event_field  
  
-   field_type  
  
-   column_type  
  
 You can use the preceding information when configuring event sessions that use the bucketing target. For more information, see [SQL Server Extended Events Targets](../../Topics/TopicNameNotContainA/SQL-Server-Extended-Events-Targets.md).  
  
## Before you Begin  
 Before you create a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Extended Events session, it is useful to get information about the fields associated with events.  
  
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
 [sys.dm_xe_objects](assetId:///5d944b99-b097-491b-8cbd-b0e42b459ec0)   
 [sys.dm_xe_packages](assetId:///2e5ecbe9-3ea8-45e6-a161-e31671a03e1d)