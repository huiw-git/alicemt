---
title: "Configure the recovery interval Server Configuration Option"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Configure the recovery interval Server Configuration Option
This topic describes how to configure the **recovery interval** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The **recovery interval** option defines an upper limit on the time recovering a database should take. The [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] uses the value specified for this option to determine approximately how often [automatic checkpoints](../../Topics/TopicNameNotContainA/Database-Checkpoints--SQL-Server-.md) to issue automatic checkpoints on a given database.  
  
 The default recovery-interval value is 0, which allows the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] to automatically configure the recovery interval. Typically, the default recovery interval results in automatic checkpoints occurring approximately once a minute for active databases and a recovery time of less than one minute. Higher values indicate the approximate maximum recovery time, in minutes. For example, setting the recovery interval to 3 indicates a maximum recovery time of approximately three minutes.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To Configure the recovery interval Server Configuration Option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the recovery interval option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The recovery interval affects only databases that use the default target recovery time (0). To override the server recovery interval on a database, configure a non-default target recovery time on the database. For more information, see [Change the Target Recovery Time of a Database (SQL Server)](../../Topics/TopicNameContainA/Change-the-Target-Recovery-Time-of-a-Database--SQL-Server-.md).  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] technician.  
  
-   Typically, we recommend that you keep the recovery interval at 0, unless you experience performance problems. If you decide to increase the recovery-interval setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance.  
  
-   If you use **sp_configure** to change the value of the **recovery interval** option to more than 60 (minutes), specify RECONFIGURE WITH OVERRIDE. WITH OVERRIDE disables configuration value checking (for values that are not valid or are nonrecommended values).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To set the recovery interval**  
  
1.  In Object Explorer, right-click server instance and select **Properties**.  
  
2.  Click the **Database settings** node.  
  
3.  Under **Recovery**, in the **Recovery interval (minutes)** box, type or select a value from 0 through 32767 to set the maximum amount of time, in minutes, that [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] should spend recovering each database at startup. The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To set the recovery interval  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to set the value of the `recovery interval` option to `3` minutes.  
  
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
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the recovery internal option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [Change the Target Recovery Time of a Database (SQL Server)](../../Topics/TopicNameContainA/Change-the-Target-Recovery-Time-of-a-Database--SQL-Server-.md)   
 [Database Checkpoints (SQL Server)](../../Topics/TopicNameNotContainA/Database-Checkpoints--SQL-Server-.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [show advanced options Server Configuration Option](../../Topics/TopicNameNotContainA/show-advanced-options-Server-Configuration-Option.md)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)