---
title: "Configure Resource Governor Using a Template"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# Configure Resource Governor Using a Template
You can configure Resource Governor by using a template that is provided in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
-   **Before you begin:**  [Permissions](#Permissions)  
  
-   **To create a workload group, using:**  [a template](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 Use the following steps to open and modify a template that creates a resource pool and a workload group for the pool. In addition, this template enables you to create a classifier user-defined function that routes new connections to either the default group or the workload group that you create.  
  
###  <a name="Permissions"></a> Permissions  
 The resource governor [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements in the template require CONTROL SERVER permission.  
  
##  <a name="ConfRGTemplate"></a> Configure Resource Governor Using a Template  
 **To configure resource governor by using a template in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]**  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], on the **View** menu, click **Template Explorer**.  
  
2.  In **Template Explorer**, expand **Resource Governor**, and then double-click **Configure Resource Governor**.  
  
3.  In **Connect to Database Engine**, enter the required information, and then click **OK**. The template Configure Resource Governor.sql is provided in the Query Editor. Use this template to create and configure a resource pool, a workload group, and a classifier function.  
  
4.  To change the values in the template, press CTRL+SHIFT+M. In the **Specify Values for Template Parameters** window, enter the values that you want to use.  
  
5.  To save the changes that you make to the template, click **OK**.  
  
6.  To run the query, click **Execute**.  
  
## See Also  
 [Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics/TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Resource Governor Resource Pool](../../Topics/TopicNameNotContainA/Resource-Governor-Resource-Pool.md)   
 [Resource Governor Workload Group](../../Topics/TopicNameNotContainA/Resource-Governor-Workload-Group.md)   
 [Resource Governor Classifier Function](../../Topics/TopicNameNotContainA/Resource-Governor-Classifier-Function.md)   
 [View Resource Governor Properties](../../Topics/TopicNameNotContainA/View-Resource-Governor-Properties.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](assetId:///82712505-c6f9-4a65-a469-f029b5a2d6cd)   
 [CREATE WORKLOAD GROUP (Transact-SQL)](assetId:///d949e540-9517-4bca-8117-ad8358848baa)   
 [CREATE FUNCTION (Transact-SQL)](assetId:///864b393f-225f-4895-8c8d-4db59ea60032)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](assetId:///442c54bf-a0a6-4108-ad20-db910ffa6e3c)