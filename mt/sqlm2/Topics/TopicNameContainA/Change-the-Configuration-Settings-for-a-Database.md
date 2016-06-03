---
title: Change the Configuration Settings for a Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
---
# Change the Configuration Settings for a Database
  This topic describes how to change database\-level options in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. These options are unique to each database and do not affect other databases.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To change the option settings for a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Only the system administrator, database owner, members of the **sysadmin** and **dbcreator** fixed server roles and **db\_owner** fixed database roles can modify these options.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To change the option settings for a database  
  
1.  In Object Explorer, connect to a [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance, expand the server, expand **Databases**, right\-click a database, and then click **Properties**.  
  
2.  In the **Database Properties** dialog box, click **Options** to access most of the configuration settings. File and filegroup configurations, mirroring and log shipping are on their respective pages.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To change the option settings for a database  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example sets the recovery model and data page verification options for the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] sample database.  
  
 [!CODE [DatabaseDDL#AlterDatabase7](../CodeSnippet/SQL15/tsql/databaseddl#alterdatabase7)]  
  
 For more examples, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
## See Also  
 [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md)   
 [ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md)   
 [Rename a Database](../../Topics\TopicNameContainA/Rename-a-Database.md)   
 [Shrink a Database](../../Topics\TopicNameContainA/Shrink-a-Database.md)  
  
  