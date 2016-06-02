---
title: Configure the query governor cost limit Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
---
# Configure the query governor cost limit Server Configuration Option
  This topic describes how to configure the **query governor cost limit** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The query governor cost limit option specifies an upper limit on the time period in which a query can run. Query cost refers to the estimated elapsed time, in seconds, that is required to complete a query on a specific hardware configuration. The default value for this option is 0, which sets the query governor to off. This allows all queries to run without any time limitation. If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost that exceeds that value.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the query governor cost limit option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the query governor cost limit option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technician.  
  
-   To change the value query governor cost limit on a per\-connection basis, use the [SET QUERY\_GOVERNOR\_COST\_LIMIT](../Topic/SET%20QUERY_GOVERNOR_COST_LIMIT%20\(Transact-SQL\).md) statement.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the query governor cost limit option  
  
1.  In Object Explorer, right\-click a server and select **Properties**.  
  
2.  Click the **Connections** page.  
  
3.  Select or clear the **Use query governor to prevent long\-running queries** check box.  
  
     If you select this check box, in the box below, enter a positive value, which the query governor uses to disallow execution of any query with a running length exceeding that value.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the query governor cost limit option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `query governor cost limit` option to `120` seconds.  
  
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
  
 For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the query governor cost limit option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](../Topic/SET%20QUERY_GOVERNOR_COST_LIMIT%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  