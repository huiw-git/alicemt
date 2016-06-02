---
title: Configure the nested triggers Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29d7372b-d406-4a5b-80c6-a2d231d25211
---
# Configure the nested triggers Server Configuration Option
  This topic describes how to configure the **nested triggers** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **nested triggers** option controls whether an AFTER trigger can cascade. That is, perform an action that initiates another trigger, which initiates another trigger, and so on. When **nested triggers** is set to 0, AFTER triggers cannot cascade. When **nested triggers** is set to 1 \(the default\), AFTER triggers can cascade to as many as 32 levels. INSTEAD OF triggers can be nested regardless of the setting of this option.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To configure the nested triggers option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the nested triggers option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the nested triggers option  
  
1.  In **Object Explorer**, right\-click a server, and then select **Properties**.  
  
2.  On the **Advanced** page, set the **Allow Triggers to Fire Others** option to **True** \(the default\) or **False**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the nested triggers option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `nested triggers` option to `0`.  
  
```wmimof  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'nested triggers', 0 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the nested triggers option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [Create Nested Triggers](../../Topics\TopicNameNotContainA/Create-Nested-Triggers.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  