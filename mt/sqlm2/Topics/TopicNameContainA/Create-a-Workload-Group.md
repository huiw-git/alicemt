---
title: Create a Workload Group
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 072868ec-ceff-4db6-941b-281af731a067
---
# Create a Workload Group
  You can create a workload group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To create a workload group, using:**  [SQL Server Management Studio](#CreRPProp), [Transact\-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="LimitationsRestrictions"></a> Limitations and Restrictions  
 **REQUEST\_MAX\_MEMORY\_GRANT\_PERCENT**  
  
 The memory consumed by index creation on a non\-aligned partitioned table is proportional to the number of partitions involved. If the total required memory exceeds the per\-query limit, \(REQUEST\_MAX\_MEMORY\_GRANT\_PERCENT\) imposed by the workload group setting, this index creation may fail. Because the default workload group allows a query to exceed the per\-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.  
  
 Index creation is allowed to use more memory workspace than initially granted for performance. This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.  
  
###  <a name="Permissions"></a> Permissions  
 Creating a workload group requires CONTROL SERVER permission.  
  
##  <a name="CreRPProp"></a> Create a Workload Group Using SQL Server Management Studio  
 **To create a workload group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]**  
  
1.  In Object Explorer, recursively expand the **Management** node down to and including the resource pool that contains the workload group to be modified.  
  
2.  Right\-click the **Workload Groups** folder, and then click **New Workload Group**.  
  
3.  In the **Resource pools** grid, ensure the resource pool where you want to add the workload group is highlighted.  
  
4.  The **Workload groups for resource pool** grid will have a new line with a blank name and default values in the other columns.  
  
5.  Click the **Name** cell and enter a name for the workload group.  
  
6.  Click or double\-click any other cells in the row you want to change from their default settings, and enter the new values.  
  
7.  To save the changes, click **OK**  
  
##  <a name="CreRPTSQL"></a> Create a Workload Group Using Transact\-SQL  
 **To create a workload group by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]**  
  
1.  Run the CREATE WORKLOAD GROUP statement specifying the property values to be set.  
  
2.  Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.  
  
### Example \(Transact\-SQL\)  
 The following example creates a workload group named `groupAdhoc` in the resource pool named `poolAdhoc`.  
  
```  
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## See Also  
 [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics\TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Create a Resource Pool](../../Topics\TopicNameContainA/Create-a-Resource-Pool.md)   
 [Change Workload Group Settings](../../Topics\TopicNameNotContainA/Change-Workload-Group-Settings.md)   
 [Create and Test a Classifier User-Defined Function](../../Topics\TopicNameContainA/Create-and-Test-a-Classifier-User-Defined-Function.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20WORKLOAD%20GROUP%20\(Transact-SQL\).md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../Topic/ALTER%20RESOURCE%20GOVERNOR%20\(Transact-SQL\).md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../Topic/CREATE%20EXTERNAL%20RESOURCE%20POOL%20\(Transact-SQL\).md)  
  
  