---
title: "Get the Configurable Parameters for the ADD TARGET Argument"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
caps.latest.revision: 15
manager: jhubbard
---
# Get the Configurable Parameters for the ADD TARGET Argument
Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
 After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   required  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 Before you create a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Extended Events session, it is useful to find out what parameters you can set when you use the ADD TARGET argument in CREATE EVENT SESSION or ALTER EVENT SESSION.  
  
### To get the configurable parameters for the ADD TARGET argument using Query Editor  
  
-   In Query Editor, issue the following statements.  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## See Also  
 [CREATE EVENT SESSION (Transact-SQL)](assetId:///67683027-2b0f-47aa-b223-604731af8b4d)   
 [ALTER EVENT SESSION (Transact-SQL)](assetId:///da006ac9-f914-4995-a2fb-25b5d971cd90)   
 [sys.dm_xe_objects](assetId:///5d944b99-b097-491b-8cbd-b0e42b459ec0)   
 [sys.dm_xe_packages](assetId:///2e5ecbe9-3ea8-45e6-a161-e31671a03e1d)