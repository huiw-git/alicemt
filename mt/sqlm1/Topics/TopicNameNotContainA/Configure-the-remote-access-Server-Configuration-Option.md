---
title: Configure the remote access Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
---
# Configure the remote access Server Configuration Option
  This topic is about the "Remote Access" feature. This is an obscure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] communication feature that is deprecated, and you probably shouldn't be using it. If you reached this page because you are having trouble connecting to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see one of the following topics instead:  
  
-   [Tutorial: Getting Started with the Database Engine](../Topic/Tutorial:%20Getting%20Started%20with%20the%20Database%20Engine.md)  
  
-   [Logging In to SQL Server](../../Topics\TopicNameNotContainA/Logging-In-to-SQL-Server.md)  
  
-   [Connect to SQL Server When System Administrators Are Locked Out](../../Topics\TopicNameNotContainA/Connect-to-SQL-Server-When-System-Administrators-Are-Locked-Out.md)  
  
-   [Connect to a Registered Server &#40;SQL Server Management Studio&#41;](../Topic/Connect%20to%20a%20Registered%20Server%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Connect to Any SQL Server Component from SQL Server Management Studio](../Topic/Connect%20to%20Any%20SQL%20Server%20Component%20from%20SQL%20Server%20Management%20Studio.md)  
  
-   [Connect to the Database Engine With sqlcmd](../../Topics\TopicNameNotContainA/Connect-to-the-Database-Engine-With-sqlcmd.md)  
  
-   [How to Troubleshoot Connecting to the SQL Server Database Engine](http://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
 Programmers may be interested in the following topics:  
  
-   [How To: Connect to SQL Server Using SQL Authentication in ASP.NET 2.0](https://msdn.microsoft.com/library/ff648340.aspx)  
  
-   [Connecting to an Instance of SQL Server](https://msdn.microsoft.com/library/ms162132.aspx)  
  
-   [How to: Create Connections to SQL Server Databases](https://msdn.microsoft.com/library/s4yys16a.aspx)  
  
 **The main body of this topic starts here.**  
  
 This topic describes how to configure the **remote access** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **remote access** option controls the execution of stored procedures from local or remote servers on which instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] are running. This default value for this option is 1. This grants permission to run local stored procedures from remote servers or remote stored procedures from the local server. To prevent local stored procedures from being run from a remote server or remote stored procedures from being run on the local server, set the option to 0.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../Token\Other/ssNoteDepNextDontUse_md.md)] Use [sp\_addlinkedserver](../Topic/sp_addlinkedserver%20\(Transact-SQL\).md) instead.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To configure the remote access option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the remote access option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The **remote access** option only applies to servers that are added by using [sp\_addserver](../Topic/sp_addserver%20\(Transact-SQL\).md), and is included for backward compatibility.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the remote access option  
  
1.  In Object Explorer, right\-click a server and select **Properties**.  
  
2.  Click the **Connections** node.  
  
3.  Under **Remote server connections**, select or clear the **Allow remote connections to this server** check box.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the remote access option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `remote access` option to `0`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the remote access option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  