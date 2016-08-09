---
title: "Configure the scan for startup procs Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# Configure the scan for startup procs Server Configuration Option
This topic describes how to configure the **scan for startup procs** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. Use the **scan for startup procs** option to scan for automatic execution of stored procedures at [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] startup time. If this option is set to 1, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] scans for and runs all automatically run stored procedures that are defined on the server. The default value for **scan for startup procs** is 0 (do not scan).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the scan for startup procs option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the scan for startup procs option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] technician.  
  
-   The value for this option can be set by using **sp_configure**; however, it will be set automatically if you use **sp_procoption**, which is used to mark or unmark automatically run stored procedures. When **sp_procoption** is used to mark the first stored procedure as an autoproc, this option is set automatically to a value of 1. When **sp_procoption** is used to unmark the last stored procedure as an autoproc, this option is automatically set to a value of 0. If you use **sp_procoption** to mark and unmark autoprocs, and if you always unmark autoprocs before dropping them, there is no need to set this option manually.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the scan for startup procs option  
  
1.  In Object Explorer, right-click a server and select **Properties**.  
  
2.  Click the **Advanced** node.  
  
3.  Under **Miscellaneous**, change the **Scan for Startup Procs** option to True or False by selecting the value you want from the drop-down list box.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the scan for startup procs option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to set the value of the `scan for startup procs` option to `1`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'scan for startup procs', 1 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the scan for startup procs option  
 The server must be restarted before the setting can take effect.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [sp_procoption (Transact-SQL)](assetId:///6f0221bd-70b4-4b04-b15d-722235aceb3c)