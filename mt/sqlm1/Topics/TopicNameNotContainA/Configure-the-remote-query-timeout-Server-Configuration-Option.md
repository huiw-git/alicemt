---
title: Configure the remote query timeout Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 888c8448-933b-41e3-8aa1-c206bc0cdb78
---
# Configure the remote query timeout Server Configuration Option
  This topic describes how to configure the **remote query timeout** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **remote query timeout** option specifies how long, in seconds, a remote operation can take before [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] times out. The default value for this option is 600, which allows a 10\-minute wait. This value applies to an outgoing connection initiated by the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] as a remote query. This value has no effect on queries received by the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. To disable the time\-out, set the value to 0. A query will wait until it is canceled.  
  
 For heterogeneous queries, **remote query timeout** specifies the number of seconds \(initialized in the command object using the DBPROP\_COMMANDTIMEOUT rowset property\) that a remote provider should wait for result sets before the query times out. This value is also used to set DBPROP\_GENERALTIMEOUT if supported by the remote provider. This will cause any other operations to time out after the specified number of seconds.  
  
 For remote stored procedures, **remote query timeout** specifies the number of seconds that must elapse after sending a remote `EXEC` statement before the remote stored procedure times out.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To configure the remote query timeout option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the remote query timeout option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Remote server connections must be allowed before this value can be set.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the remote query timeout option  
  
1.  In Object Explorer, right\-click a server and select **Properties**.  
  
2.  Click the **Connections** node.  
  
3.  Under **Remote server connections**, in the **Remote query timeout** box, type or select a value from 0 through 2,147,483,647 to set the maximum number seconds for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to wait before timing out.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the remote query timeout option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `remote query timeout` option to `0` to disable the time\-out.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote query timeout', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the remote query timeout option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Rowset Properties and Behaviors](../Topic/Rowset%20Properties%20and%20Behaviors.md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  