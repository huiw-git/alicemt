---
title: Get the Configurable Parameters for the ADD TARGET Argument
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
---
# Get the Configurable Parameters for the ADD TARGET Argument
  Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:  
  
-   package\_name  
  
-   target\_name  
  
-   parameter\_name  
  
-   parameter\_type  
  
-   required  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 Before you create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events session, it is useful to find out what parameters you can set when you use the ADD TARGET argument in CREATE EVENT SESSION or ALTER EVENT SESSION.  
  
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
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../Topic/CREATE%20EVENT%20SESSION%20\(Transact-SQL\).md)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../Topic/ALTER%20EVENT%20SESSION%20\(Transact-SQL\).md)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](../Topic/sys.dm_xe_objects%20\(Transact-SQL\).md)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](../Topic/sys.dm_xe_packages%20\(Transact-SQL\).md)  
  
  