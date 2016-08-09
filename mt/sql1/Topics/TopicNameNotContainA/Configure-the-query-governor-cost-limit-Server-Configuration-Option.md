---
title: "Configure the query governor cost limit Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# Configure the query governor cost limit Server Configuration Option
This topic describes how to configure the **query governor cost limit** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The query governor cost limit option specifies an upper limit on the time period in which a query can run. Query cost refers to the estimated elapsed time, in seconds, that is required to complete a query on a specific hardware configuration. The default value for this option is 0, which sets the query governor to off. This allows all queries to run without any time limitation. If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost that exceeds that value.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the query governor cost limit option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the query governor cost limit option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] technician.  
  
-   To change the value query governor cost limit on a per-connection basis, use the [SET QUERY_GOVERNOR_COST_LIMIT](assetId:///3424bb44-6915-462d-a8d7-fe834af81387) statement.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the query governor cost limit option  
  
1.  In Object Explorer, right-click a server and select **Properties**.  
  
2.  Click the **Connections** page.  
  
3.  Select or clear the **Use query governor to prevent long-running queries** check box.  
  
     If you select this check box, in the box below, enter a positive value, which the query governor uses to disallow execution of any query with a running length exceeding that value.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the query governor cost limit option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to set the value of the `query governor cost limit` option to `120` seconds.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the query governor cost limit option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)](assetId:///3424bb44-6915-462d-a8d7-fe834af81387)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)