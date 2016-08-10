---
title: "View the Extended Events Targets for Registered Packages"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# View the Extended Events Targets for Registered Packages
Before you create a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Extended Events session, it is useful to determine what Extended Events targets are available. This task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to perform the following procedure.  
  
 After the statements in this procedure finish, the **Results** tab of Query Editor displays the following two columns:  
  
-   package_name  
  
-   target_name  
  
## To view the Extended Events targets for registered packages using Query Editor  
  
-   In Query Editor, issue the following statements.  
  
    ```  
    USE msdb  
    SELECT p.name package_name, o.name target_name  
    FROM sys.dm_xe_objects o  
    JOIN sys.dm_xe_packages p  
         ON o.package_guid = p.guid  
    WHERE o.object_type = 'target'  
    ```  
  
## See Also  
 [SQL Server Extended Events Targets](../../Topics/TopicNameNotContainA/SQL-Server-Extended-Events-Targets.md)   
 [sys.dm_xe_objects](assetId:///5d944b99-b097-491b-8cbd-b0e42b459ec0)   
 [sys.dm_xe_packages](assetId:///2e5ecbe9-3ea8-45e6-a161-e31671a03e1d)