---
title: "Configure the user connections Server Configuration Option"
ms.custom: na
ms.date: 2015-12-02
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 53beee6e-59fe-4276-9abb-8f1cec2a3508
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Configure the user connections Server Configuration Option
This topic describes how to set the **user connections** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The **user connections** option specifies the maximum number of simultaneous user connections that are allowed on an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The actual number of user connections allowed also depends on the version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that you are using, and also the limits of your application or applications and hardware. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] allows a maximum of 32,767 user connections. Because **user connections** is a dynamic (self-configuring) option, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] adjusts the maximum number of user connections automatically as needed, up to the maximum value allowable. For example, if only 10 users are logged in, 10 user connection objects are allocated. In most cases, you do not have to change the value for this option. The default is 0, which means that the maximum (32,767) user connections are allowed.  
  
 To determine the maximum number of user connections that your system allows, you can execute [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) or query the [sys.configuration](assetId:///c4709ed1-bf88-4458-9e98-8e9b78150441) catalog view.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the user connections option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the user connections option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] technician.  
  
-   Using the **user connections** option helps avoid overloading the server with too many concurrent connections. You can estimate the number of connections based on system and user requirements. For example, on a system with many users, each user would not usually require a unique connection. Connections can be shared among users. Users running OLE DB applications need a connection for each open connection object, users running Open Database Connectivity (ODBC) applications need a connection for each active connection handle in the application, and users running DB-Library applications need one connection for each process started that calls the DB-Library **dbopen** function.  
  
    > [!IMPORTANT]  
    >  If you must use this option, do not set the value too high, because each connection has overhead regardless of whether the connection is being used. If you exceed the maximum number of user connections, you receive an error message and are not able to connect until another connection becomes available.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the user connections option  
  
1.  In Object Explorer, right-click a server and click **Properties**.  
  
2.  Click the **Connections** node.  
  
3.  Under **Connections**, in the **Max number of concurrent connections** box, type or select a value from 0 through 32767 to set the maximum number of users that are allowed to connect simultaneously to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
4.  Restart [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the user connections option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to configure the value of the `user connections` option to `325` users.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'user connections', 325 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the user connections option  
 The server must be restarted before the setting can take effect.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)