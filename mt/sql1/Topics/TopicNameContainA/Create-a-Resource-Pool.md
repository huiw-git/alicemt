---
title: "Create a Resource Pool"
ms.custom: na
ms.date: 2016-03-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Create a Resource Pool
You can create a resource pool by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. To understand the principals of resource pools, see [Resource Governor Resource Pool](../../Topics/TopicNameNotContainA/Resource-Governor-Resource-Pool.md).  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To create a resource pool, using:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="LimitationsRestrictions"></a> Limitations and Restrictions  
 The maximum CPU percentage must be equal to or higher than the minimum CPU percentage. The maximum memory percentage must be equal to or higher than the minimum memory percentage.  
  
 The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.  
  
###  <a name="Permissions"></a> Permissions  
 Creating a resource pool requires CONTROL SERVER permission.  
  
##  <a name="CreRPProp"></a> Create a Resource Pool Using SQL Server Management Studio  
 **To create a resource pool by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]**  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.  
  
2.  Right-click **Resource Governor**, and then click **Properties**.  
  
3.  In the **Resource pools** grid, click the first column in the empty row. This column is labeled with an asterisk (*).  
  
4.  Double-click the empty cell in the **Name** column. Type in the name that you want to use for the resource pool.  
  
5.  Click or double-click any other cells in the row you want to change, and enter the new values.  
  
6.  To save the changes, click **OK**  
  
##  <a name="CreRPTSQL"></a> Create a Resource Pool Using Transact-SQL  
 **To create a resource pool by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]**  
  
1.  Run the [CREATE RESOURCE POOL](assetId:///82712505-c6f9-4a65-a469-f029b5a2d6cd) or [CREATE EXTERNAL RESOURCE POOL](assetId:///8cc798ad-c395-461c-b7ff-8c561c098808) statement specifying the property values to be set.  
  
2.  Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.  
  
### Example (Transact-SQL)  
 The following example creates a resource pool named `poolAdhoc`.  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## See Also  
 [Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics/TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Resource Governor Resource Pool](../../Topics/TopicNameNotContainA/Resource-Governor-Resource-Pool.md)   
 [Change Resource Pool Settings](../../Topics/TopicNameNotContainA/Change-Resource-Pool-Settings.md)   
 [Delete a Resource Pool](../../Topics/TopicNameContainA/Delete-a-Resource-Pool.md)   
 [Configure Resource Governor Using a Template](../../Topics/TopicNameContainA/Configure-Resource-Governor-Using-a-Template.md)   
 [Resource Governor Workload Group](../../Topics/TopicNameNotContainA/Resource-Governor-Workload-Group.md)   
 [Resource Governor Classifier Function](../../Topics/TopicNameNotContainA/Resource-Governor-Classifier-Function.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](assetId:///82712505-c6f9-4a65-a469-f029b5a2d6cd)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](assetId:///442c54bf-a0a6-4108-ad20-db910ffa6e3c)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](assetId:///8cc798ad-c395-461c-b7ff-8c561c098808)   
 [ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](assetId:///634c327d-971b-49ba-b8a2-e243a04040db)