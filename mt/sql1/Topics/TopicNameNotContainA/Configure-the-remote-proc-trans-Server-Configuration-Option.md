---
title: "Configure the remote proc trans Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Configure the remote proc trans Server Configuration Option
This topic describes how to configure the **remote proc trans** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The **remote proc trans** option helps protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Distributed Transaction Coordinator (MS DTC) transaction.  
  
 Set the value of **remote proc trans** to 1 to provide an MS DTC-coordinated distributed transaction that protects the ACID (atomic, consistent, isolated, and durable) properties of transactions. Sessions begun after setting this option to 1 inherit the configuration setting as their default.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../Topics/TopicNameNotContainA/tokens/ssNoteDepNextAvoid_md.md)]  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the remote proc trans option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the remote proc trans option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Remote server connections must be allowed before this value can be set.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is provided for compatibility with earlier versions of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] for applications that use remote stored procedures. Instead of issuing remote stored procedure calls, use distributed queries that reference linked servers, which are defined by using [sp_addlinkedserver](assetId:///fed3adb0-4c15-4a1a-8acd-1b184aff558f).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the remote proc trans option  
  
1.  In Object Explorer, right-click a server and select **Properties**.  
  
2.  Click the **Connections** node.  
  
3.  Under **Remote server connections**, select the **Require Distributed Transactions for server to server communication** check box.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the remote proc trans option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to set the value of the `remote proc trans` option to `1`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the remote proc trans option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)