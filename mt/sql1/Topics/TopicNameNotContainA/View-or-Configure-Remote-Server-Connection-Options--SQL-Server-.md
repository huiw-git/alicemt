---
title: "View or Configure Remote Server Connection Options (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# View or Configure Remote Server Connection Options (SQL Server)
This topic describes how to view or configure remote server connection options at the server level in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view or configure remote server connection options, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure remote server connection options](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Executing **sp_serveroption** requires ALTER ANY LINKED SERVER permission on the server.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view or configure remote server connection options  
  
1.  In Object Explorer, right-click a server, and then click **Properties**.  
  
2.  In the **SQL Server Properties - <***server_name***>** dialog box, click **Connections**.  
  
3.  On the **Connections** page, review the **Remote server connections** settings, and modify them if necessary.  
  
4.  Repeat steps 1 through 3 on the other server of the remote server pair.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To view remote server connection options  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses [sp_helpserver](assetId:///e8f42de7-c738-41c3-8bf5-dbd559dc7184) to return information about all remote servers.  
  
```tsql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### To configure remote server connection options  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_serveroption](assetId:///47d04a2b-dbf0-4f15-bd9b-81a2efc48131) to configure a remote server. The example configures a remote server corresponding to another instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], `SEATTLE3`, to be collation compatible with the local instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
```tsql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="FollowUp"></a> Follow Up: After you configure remote server connection options  
 The remote server must be stopped and restarted before the setting can take effect.  
  
## See Also  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [Remote Servers](../../Topics/TopicNameNotContainA/Remote-Servers.md)   
 [Linked Servers (Database Engine)](../../Topics/TopicNameNotContainA/Linked-Servers--Database-Engine-.md)   
 [sp_linkedservers (Transact-SQL)](assetId:///d8f82f78-8a1f-4831-bcee-7c36c6e7dfbb)   
 [sp_helpserver (Transact-SQL)](assetId:///e8f42de7-c738-41c3-8bf5-dbd559dc7184)   
 [sp_serveroption (Transact-SQL)](assetId:///47d04a2b-dbf0-4f15-bd9b-81a2efc48131)