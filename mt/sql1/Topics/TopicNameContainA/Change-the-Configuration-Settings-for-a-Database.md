---
title: "Change the Configuration Settings for a Database"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Change the Configuration Settings for a Database
This topic describes how to change database-level options in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. These options are unique to each database and do not affect other databases.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To change the option settings for a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Only the system administrator, database owner, members of the **sysadmin** and **dbcreator** fixed server roles and **db_owner** fixed database roles can modify these options.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To change the option settings for a database  
  
1.  In Object Explorer, connect to a [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] instance, expand the server, expand **Databases**, right-click a database, and then click **Properties**.  
  
2.  In the **Database Properties** dialog box, click **Options** to access most of the configuration settings. File and filegroup configurations, mirroring and log shipping are on their respective pages.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To change the option settings for a database  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example sets the recovery model and data page verification options for the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] sample database.  
  
 [!CODE [DatabaseDDL#AlterDatabase7](../CodeSnippet/SQL15/tsql/databaseddl#alterdatabase7)]  
  
 For more examples, see [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc).  
  
## See Also  
 [ALTER DATABASE Compatibility Level (Transact-SQL)](assetId:///ca5fd220-d5ea-4182-8950-55d4101a86f6)   
 [ALTER DATABASE Database Mirroring (Transact-SQL)](assetId:///27a032ef-1cf6-4959-8e67-03d28c4b3465)   
 [ALTER DATABASE SET HADR (Transact-SQL)](assetId:///20e6e803-d6d5-48d5-b626-d1e0a73d174c)   
 [Rename a Database](../../Topics/TopicNameContainA/Rename-a-Database.md)   
 [Shrink a Database](../../Topics/TopicNameContainA/Shrink-a-Database.md)