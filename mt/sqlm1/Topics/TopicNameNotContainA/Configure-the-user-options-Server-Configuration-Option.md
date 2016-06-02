---
title: Configure the user options Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfed8f86-6bcf-4b90-88eb-9656e22d5dc5
---
# Configure the user options Server Configuration Option
  This topic describes how to configure the **user options** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **user options** option specifies global defaults for all users. A list of default query processing options is established for the duration of a user's work session. The **user options** option allows you to change the default values of the SET options \(if the server's default settings are not appropriate\).  
  
 A user can override these defaults by using the SET statement. You can configure **user options** dynamically for new logins. After you change the setting of **user options**, new login sessions use the new setting; current login sessions are not affected.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the user options configuration option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the user options configuration option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   The following table lists and describes the configuration values for **user options**. Not all configuration values are compatible with each other. For example, ANSI\_NULL\_DFLT\_ON and ANSI\_NULL\_DFLT\_OFF cannot be set at the same time.  
  
    |Value|Configuration|Description|  
    |-----------|-------------------|-----------------|  
    |1|DISABLE\_DEF\_CNST\_CHK|Controls interim or deferred constraint checking.|  
    |2|IMPLICIT\_TRANSACTIONS|For dblib network library connections, controls whether a transaction is started implicitly when a statement is executed. The IMPLICIT\_TRANSACTIONS setting has no effect on ODBC or OLEDB connections.|  
    |4|CURSOR\_CLOSE\_ON\_COMMIT|Controls behavior of cursors after a commit operation has been performed.|  
    |8|ANSI\_WARNINGS|Controls truncation and NULL in aggregate warnings.|  
    |16|ANSI\_PADDING|Controls padding of fixed\-length variables.|  
    |32|ANSI\_NULLS|Controls NULL handling when using equality operators.|  
    |64|ARITHABORT|Terminates a query when an overflow or divide\-by\-zero error occurs during query execution.|  
    |128|ARITHIGNORE|Returns NULL when an overflow or divide\-by\-zero error occurs during a query.|  
    |256|QUOTED\_IDENTIFIER|Differentiates between single and double quotation marks when evaluating an expression.|  
    |512|NOCOUNT|Turns off the message returned at the end of each statement that states how many rows were affected.|  
    |1024|ANSI\_NULL\_DFLT\_ON|Alters the session's behavior to use ANSI compatibility for nullability. New columns defined without explicit nullability are defined to allow nulls.|  
    |2048|ANSI\_NULL\_DFLT\_OFF|Alters the session's behavior not to use ANSI compatibility for nullability. New columns defined without explicit nullability do not allow nulls.|  
    |4096|CONCAT\_NULL\_YIELDS\_NULL|Returns NULL when concatenating a NULL value with a string.|  
    |8192|NUMERIC\_ROUNDABORT|Generates an error when a loss of precision occurs in an expression.|  
    |16384|XACT\_ABORT|Rolls back a transaction if a Transact\-SQL statement raises a run\-time error.|  
  
-   The bit positions in **user options** are identical to those in @@OPTIONS. Each connection has its own @@OPTIONS function, which represents the configuration environment. When logging in to an instance of \\ [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], a user receives a default environment that assigns the current **user options** value to @@OPTIONS. Executing SET statements for **user options** affects the corresponding value in the session's @@OPTIONS function. All connections created after this setting is changed receive the new value.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the user options configuration option  
  
1.  In Object Explorer, right\-click a server and select **Properties**.  
  
2.  Click the **Connections** node.  
  
3.  In the **Default connection options** box, select one or more attributes to configure the default query\-processing options for all connected users.  
  
     By default, no user options are configured.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the user options configuration option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to configure the `user options` to change the setting for the ANSI\_WARNINGS server option.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'user options', 8 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the user options configuration option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [SET Statements &#40;Transact-SQL&#41;](../Topic/SET%20Statements%20\(Transact-SQL\).md)  
  
  