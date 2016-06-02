---
title: Move a Workload Group
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
---
# Move a Workload Group
  You can move a Resource Governor workload group to a different resource pool by using either [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or Transact\-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To move a workload group, using:**  [SQL Server Management Studio](#MoveWGSSMS), [Transact\-SQL](#MoveWGTSQL)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 You cannot move a workload group if there is a pending Resource Governor configuration operation.  
  
###  <a name="LimitationsRestrictions"></a> Limitations and Restrictions  
 You cannot move a workload group if there is a pending Resource Governor configuration operation. You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](../Topic/sys.dm_resource_governor_configuration%20\(Transact-SQL\).md) dynamic management view to get the current status of is\_configuration\_pending.  
  
###  <a name="Permissions"></a> Permissions  
 Moving a workload group requires CONTROL SERVER permission.  
  
##  <a name="MoveWGSSMS"></a> Move a Workload Group Using SQL Server Management Studio  
 **To move a workload group by using [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]**  
  
1.  In Object Explorer, recursively expand the **Management** node down to **Resource Governor**.  
  
2.  Right\-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.  
  
3.  In the **Resource Pools** window, click the resource pool containing the workload group to be moved. The **Workload Groups** window now lists the workload groups in that resource pool.  
  
4.  In the **Workload Groups** window, right\-click the right arrow to the left of the workload group to be moved, and click **Move to**. This displays a **Move Workload Group** window.  
  
5.  Available resource pools are displayed in the window. Click the name of the resource pool that you want to move the workload group to, and then click **OK** to carry out this action.  
  
6.  This action is not completed until after you click **OK**. When you click **OK**, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.  
  
7.  If the create or reconfigure operation fails for the resource pool or workload group, a summary error message appears below the title of the property page. To see a detailed error message, click the down arrow on the error message.  
  
##  <a name="MoveWGTSQL"></a> Move a Workload Group Using Transact\-SQL  
 **To move a workload group by using Transact\-SQL**  
  
1.  Run the **ALTER WORKLOAD GROUP** statement specifying the name of the workload group to be moved and the resource pool to which it should be moved.  
  
2.  Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.  
  
### Example \(Transact\-SQL\)  
 The following example moves a workload group named `groupAdhoc` to the default resource pool.  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## See Also  
 [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics\TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Create a Resource Pool](../../Topics\TopicNameContainA/Create-a-Resource-Pool.md)   
 [Create a Workload Group](../../Topics\TopicNameContainA/Create-a-Workload-Group.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20WORKLOAD%20GROUP%20\(Transact-SQL\).md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../Topic/ALTER%20RESOURCE%20GOVERNOR%20\(Transact-SQL\).md)  
  
  