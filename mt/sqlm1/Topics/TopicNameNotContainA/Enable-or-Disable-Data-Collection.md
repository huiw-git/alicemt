---
title: Enable or Disable Data Collection
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
---
# Enable or Disable Data Collection
  This topic describes how to enable or disable data collection in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To enable or disable data collection, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the **dc\_admin** or **dc\_operator** \(with EXECUTE permission\) fixed database role to execute this procedure.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To enable the data collector  
  
1.  In Object Explorer, expand the **Management** node.  
  
2.  Right\-click **Data Collection**, and then click **Enable Data Collection**.  
  
#### To disable the data collector  
  
1.  In Object Explorer, expand the **Management** node.  
  
2.  Right\-click **Data Collection**, and then click **Disable Data Collection**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To enable the data collector  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses [sp\_syscollector\_enable\_collector](../Topic/sp_syscollector_enable_collector%20\(Transact-SQL\).md) to enable the data collector.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### To disable the data collector  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses [sp\_syscollector\_disable\_collector](../Topic/sp_syscollector_disable_collector%20\(Transact-SQL\).md) to disable the data collector.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## See Also  
 [Data Collection](../../Topics\TopicNameNotContainA/Data-Collection.md)   
 [System Stored Procedures &#40;Transact-SQL&#41;](../Topic/System%20Stored%20Procedures%20\(Transact-SQL\).md)  
  
  