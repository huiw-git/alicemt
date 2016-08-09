---
title: "Change Resource Pool Settings"
ms.custom: na
ms.date: 2016-03-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# Change Resource Pool Settings
You can change resource pool settings by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To change the settings for a resource pool, using:**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="LimitationsRestrictions"></a> Limitations and Restrictions  
 The maximum CPU percentage must be equal to or higher than the minimum CPU percentage. The maximum memory percentage must be equal to or higher than the minimum memory percentage.  
  
 The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.  
  
###  <a name="Permissions"></a> Permissions  
 Changing resource pool settings requires CONTROL SERVER permission.  
  
##  <a name="ChgRPProp"></a> Change Resource Pool Settings Using SQL Server Management Studio  
 **To change resource pool settings by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]**  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.  
  
2.  Right-click the resource pool to be modified, and then click **Properties**.  
  
3.  In the **Resource Governor Properties** page, select the row for the resource pool in the **Resource pools** grid if it is not automatically selected.  
  
4.  Click or double-click the cells in the row to be changed, and enter the new values.  
  
5.  To save the changes, click **OK**  
  
##  <a name="ChgRPTSQL"></a> Change Resource Pool Settings Using Transact-SQL  
 **To change resource pool settings by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]**  
  
1.  Run the **ALTER RESOURCE POOL** or **ALTER EXTERNAL RESOURCE POOL** statement specifying the property values to be changed.  
  
2.  Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.  
  
### Example (Transact-SQL)  
 The following example changes the max CPU percentage setting for the resource pool named `poolAdhoc`.  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## See Also  
 [Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics/TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Create a Resource Pool](../../Topics/TopicNameContainA/Create-a-Resource-Pool.md)   
 [Delete a Resource Pool](../../Topics/TopicNameContainA/Delete-a-Resource-Pool.md)   
 [Resource Governor Workload Group](../../Topics/TopicNameNotContainA/Resource-Governor-Workload-Group.md)   
 [Resource Governor Classifier Function](../../Topics/TopicNameNotContainA/Resource-Governor-Classifier-Function.md)   
 [ALTER RESOURCE POOL (Transact-SQL)](assetId:///9c1c4cfb-0e3b-4f01-bf57-3fce94c7d1d4)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](assetId:///442c54bf-a0a6-4108-ad20-db910ffa6e3c)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](assetId:///8cc798ad-c395-461c-b7ff-8c561c098808)   
 [ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](assetId:///634c327d-971b-49ba-b8a2-e243a04040db)