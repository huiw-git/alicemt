---
title: "Enable or Disable Data Collection"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
caps.latest.revision: 19
caps.handback.revision: 0
manager: jhubbard
---
# Enable or Disable Data Collection
This topic describes how to enable or disable data collection in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To enable or disable data collection, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the **dc_admin** or **dc_operator** (with EXECUTE permission) fixed database role to execute this procedure.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To enable the data collector  
  
1.  In Object Explorer, expand the **Management** node.  
  
2.  Right-click **Data Collection**, and then click **Enable Data Collection**.  
  
#### To disable the data collector  
  
1.  In Object Explorer, expand the **Management** node.  
  
2.  Right-click **Data Collection**, and then click **Disable Data Collection**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To enable the data collector  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses [sp_syscollector_enable_collector](assetId:///53ff2b0d-b7da-4e3d-8f3d-35e857bc3720) to enable the data collector.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### To disable the data collector  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses [sp_syscollector_disable_collector](assetId:///9ef4c85d-cca6-452d-94be-2be6f616c3d8) to disable the data collector.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## See Also  
 [Data Collection](../../Topics/TopicNameNotContainA/Data-Collection.md)   
 [System Stored Procedures (Transact-SQL)](assetId:///a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a)