---
title: "Configure the index create memory Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Configure the index create memory Server Configuration Option
This topic describes how to configure the **index create memory** server configuration option in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The **index create memory** option controls the maximum amount of memory initially allocated for creating indexes. The default value for this option is 0 (self-configuring). If more memory is later needed for index creation and the memory is available, the server will use it; thereby, exceeding the setting of this option. If additional memory is not available, the index creation will continue using the memory already allocated.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the index create memory option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the index create memory option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The setting of the **min memory per query** option has precedence over the **index create memory** option. If you change both options and the **index create memory** is less than **min memory per query**, you receive a warning message, but the value is set. During query execution, you receive a similar warning.  
  
-   When using partitioned tables and indexes, the minimum memory requirements for index creation may increase significantly if there are non-aligned partitioned indexes and a high degree of parallelism. This option controls the total initial amount of memory allocated for all index partitions in a single index creation operation. The query will terminate with an error message if the amount set by this option is less than the minimum required to run the query.  
  
-   The run value for this option will not exceed the actual amount of memory that can be used for the operating system and hardware platform on which [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is running.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] technician.  
  
-   The **index create memory** option is self-configuring and usually works without requiring adjustment. However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the index create memory option  
  
1.  In Object Explorer, right-click a server and select **Properties**.  
  
2.  Click the **Memory** node.  
  
3.  Under **Index creation memory**, type or select the desired value for the index create memory option.  
  
     Use the **index create memory** option to control the amount of memory used by index creation sorts. The **index create memory** option is self-configuring and should work in most cases without requiring adjustment. However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value. Query sorts are controlled through the **min memory per query** option.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure the index create memory option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to set the value of the `index create memory` option to `4096`.  
  
```tsql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the index create memory option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [sys.configurations (Transact-SQL)](assetId:///c4709ed1-bf88-4458-9e98-8e9b78150441)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Memory Server Configuration Options](../../Topics/TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)