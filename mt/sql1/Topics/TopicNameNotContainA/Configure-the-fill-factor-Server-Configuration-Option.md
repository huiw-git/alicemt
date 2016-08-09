---
title: "Configure the fill factor Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b920ec34-ba8b-4bb8-af53-a3ffd06bafa6
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Configure the fill factor Server Configuration Option
This topic describes how to configure the **fill factor** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. Fill factor is provided for fine-tuning index data storage and performance. When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the rest as free space for future growth. For more information, see [Specify Fill Factor for an Index](../../Topics/TopicNameNotContainA/Specify-Fill-Factor-for-an-Index.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the fill factor option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the fill factor option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] technician.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the fill factor option  
  
1.  In Object Explorer, right-click a server and select **Properties**.  
  
2.  Click the **Database Settings** node.  
  
3.  In the **Default index fill factor** box, type or select the index fill factor that you want.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the fill factor option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to set the value of the `fill factor` option to `100`.  
  
```tsql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the fill factor option  
 The server must be restarted before the setting can take effect.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [ALTER INDEX (Transact-SQL)](assetId:///b796c829-ef3a-405c-a784-48286d4fb2b9)   
 [CREATE INDEX (Transact-SQL)](assetId:///d2297805-412b-47b5-aeeb-53388349a5b9)   
 [Specify Fill Factor for an Index](../../Topics/TopicNameNotContainA/Specify-Fill-Factor-for-an-Index.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [sys.indexes](assetId:///066bd9ac-6554-4297-88fe-d740de1f94a8)