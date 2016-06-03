---
title: Configure Resource Governor Using a Template
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
---
# Configure Resource Governor Using a Template
  You can configure Resource Governor by using a template that is provided in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
-   **Before you begin:**  [Permissions](#Permissions)  
  
-   **To create a workload group, using:**  [a template](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 Use the following steps to open and modify a template that creates a resource pool and a workload group for the pool. In addition, this template enables you to create a classifier user\-defined function that routes new connections to either the default group or the workload group that you create.  
  
###  <a name="Permissions"></a> Permissions  
 The resource governor [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements in the template require CONTROL SERVER permission.  
  
##  <a name="ConfRGTemplate"></a> Configure Resource Governor Using a Template  
 **To configure resource governor by using a template in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]**  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], on the **View** menu, click **Template Explorer**.  
  
2.  In **Template Explorer**, expand **Resource Governor**, and then double\-click **Configure Resource Governor**.  
  
3.  In **Connect to Database Engine**, enter the required information, and then click **OK**. The template Configure Resource Governor.sql is provided in the Query Editor. Use this template to create and configure a resource pool, a workload group, and a classifier function.  
  
4.  To change the values in the template, press CTRL\+SHIFT\+M. In the **Specify Values for Template Parameters** window, enter the values that you want to use.  
  
5.  To save the changes that you make to the template, click **OK**.  
  
6.  To run the query, click **Execute**.  
  
## See Also  
 [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics\TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Resource Governor Resource Pool](../../Topics\TopicNameNotContainA/Resource-Governor-Resource-Pool.md)   
 [Resource Governor Workload Group](../../Topics\TopicNameNotContainA/Resource-Governor-Workload-Group.md)   
 [Resource Governor Classifier Function](../../Topics\TopicNameNotContainA/Resource-Governor-Classifier-Function.md)   
 [View Resource Governor Properties](../../Topics\TopicNameNotContainA/View-Resource-Governor-Properties.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../Topic/CREATE%20RESOURCE%20POOL%20\(Transact-SQL\).md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20WORKLOAD%20GROUP%20\(Transact-SQL\).md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../Topic/CREATE%20FUNCTION%20\(Transact-SQL\).md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../Topic/ALTER%20RESOURCE%20GOVERNOR%20\(Transact-SQL\).md)  
  
  