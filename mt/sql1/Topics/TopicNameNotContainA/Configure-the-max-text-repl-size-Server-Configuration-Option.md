---
title: "Configure the max text repl size Server Configuration Option"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3056cf64-621d-4996-9162-3913f6bc6d5b
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# Configure the max text repl size Server Configuration Option
This topic describes how to configure the **max text repl size** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The **max text repl size** option specifies the maximum size (in bytes) of **text**, **ntext**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, and **image** data that can be added to a replicated column or captured column in a single INSERT, UPDATE, WRITETEXT, or UPDATETEXT statement. The default value is 65536 bytes. A value of -1 indicates that there is no size limit, other than the limit imposed by the data type.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To configure the max text repl size option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the max text repl size option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   This option applies to transactional replication and Change Data Capture. When a server is configured for both transactional replication and Change Data Capture, the specified value applies to both features. This option is ignored by snapshot replication and merge replication.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the max text repl size option  
  
1.  In Object Explorer, right-click a server and select **Properties**.  
  
2.  Click the **Advanced** node.  
  
3.  Under **Miscellaneous**, change the **Max Text Replication Size** option to the desired value.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the max text repl size option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to configure the `max text repl size` option to `-1`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;   
RECONFIGURE ;   
GO  
EXEC sp_configure 'max text repl size', -1 ;   
GO  
RECONFIGURE;   
GO  
  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the max text repl size option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [Replication Features and Tasks](../../Topics/TopicNameNotContainA/Replication-Features-and-Tasks.md)   
 [INSERT (Transact-SQL)](assetId:///1054c76e-0fd5-4131-8c07-a6c5d024af50)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [UPDATE (Transact-SQL)](assetId:///40e63302-0c68-4593-af3e-6d190181fee7)   
 [UPDATETEXT (Transact-SQL)](assetId:///d73c28ee-3972-4afd-af8d-ebbbd9e50793)   
 [WRITETEXT (Transact-SQL)](assetId:///80c252fd-a8b8-4a2e-888a-059081ed4109)