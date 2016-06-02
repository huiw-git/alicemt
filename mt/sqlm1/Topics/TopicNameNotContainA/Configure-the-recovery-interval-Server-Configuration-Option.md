---
title: Configure the recovery interval Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
---
# Configure the recovery interval Server Configuration Option
  This topic describes how to configure the **recovery interval** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **recovery interval** option defines an upper limit on the time recovering a database should take. The [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] uses the value specified for this option to determine approximately how often [automatic checkpoints](../Topic/Database%20Checkpoints%20\(SQL%20Server\).md) to issue automatic checkpoints on a given database.  
  
 The default recovery\-interval value is 0, which allows the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to automatically configure the recovery interval. Typically, the default recovery interval results in automatic checkpoints occurring approximately once a minute for active databases and a recovery time of less than one minute. Higher values indicate the approximate maximum recovery time, in minutes. For example, setting the recovery interval to 3 indicates a maximum recovery time of approximately three minutes.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To Configure the recovery interval Server Configuration Option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the recovery interval option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The recovery interval affects only databases that use the default target recovery time \(0\). To override the server recovery interval on a database, configure a non\-default target recovery time on the database. For more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../Topic/Change%20the%20Target%20Recovery%20Time%20of%20a%20Database%20\(SQL%20Server\).md).  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technician.  
  
-   Typically, we recommend that you keep the recovery interval at 0, unless you experience performance problems. If you decide to increase the recovery\-interval setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance.  
  
-   If you use **sp\_configure** to change the value of the **recovery interval** option to more than 60 \(minutes\), specify RECONFIGURE WITH OVERRIDE. WITH OVERRIDE disables configuration value checking \(for values that are not valid or are nonrecommended values\).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To set the recovery interval**  
  
1.  In Object Explorer, right\-click server instance and select **Properties**.  
  
2.  Click the **Database settings** node.  
  
3.  Under **Recovery**, in the **Recovery interval \(minutes\)** box, type or select a value from 0 through 32767 to set the maximum amount of time, in minutes, that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] should spend recovering each database at startup. The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To set the recovery interval  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `recovery interval` option to `3` minutes.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the recovery internal option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../Topic/Change%20the%20Target%20Recovery%20Time%20of%20a%20Database%20\(SQL%20Server\).md)   
 [Database Checkpoints &#40;SQL Server&#41;](../Topic/Database%20Checkpoints%20\(SQL%20Server\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [show advanced options Server Configuration Option](../../Topics\TopicNameNotContainA/show-advanced-options-Server-Configuration-Option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)  
  
  