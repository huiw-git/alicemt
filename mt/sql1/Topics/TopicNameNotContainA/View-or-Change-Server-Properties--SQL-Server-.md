---
title: "View or Change Server Properties (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# View or Change Server Properties (SQL Server)
This topic describes how to view or change the properties of an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], or SQL Server Configuration Manager.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To view or change server properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SQL Server Configuration Manager](#PowerShellProcedure)  
  
-   **Follow Up:**  [After you change server properties](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   When using sp_configure, you must run either RECONFIGURE or RECONFIGURE WITH OVERRIDE after setting a configuration option. The RECONFIGURE WITH OVERRIDE statement is usually reserved for configuration options that should be used with extreme caution. However, RECONFIGURE WITH OVERRIDE works for all configuration options, and you can use it in place of RECONFIGURE.  
  
    > [!NOTE]  
    >  RECONFIGURE executes within a transaction. If any of the reconfigure operations fail, none of the reconfigure operations will take effect.  
  
-   Some property pages present information obtained via Windows Management Instrumentation (WMI). To display those pages, WMI must be installed on the computer running [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 For more information, see [Server-Level Roles](../../Topics/TopicNameNotContainA/Server-Level-Roles.md).  
  
 Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view or change server properties  
  
1.  In Object Explorer, right-click a server, and then click **Properties**.  
  
2.  In the **Server Properties** dialog box, click a page to view or change server information about that page. Some properties are read-only.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To view server properties by using the SERVERPROPERTY built-in function  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses the [SERVERPROPERTY](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a) built-in function in a `SELECT` statement to return information about the current server. This scenario is useful when there are multiple instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installed on a Windows-based server, and the client must open another connection to the same instance that is used by the current connection.  
  
    ```tsql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### To view server properties by using the sys.servers catalog view  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example queries the [sys.servers](assetId:///4e774ed9-4e83-4726-9f1d-8efde8f9feff) catalog view to return the name (`name`) and ID (`server_id`) of the current server, and the name of the OLE DB provider (`provider`) for connecting to a linked server.  
  
    ```tsql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO  
  
    ```  
  
#### To view server properties by using the sys.configurations catalog view  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example queries the [sys.configurations](assetId:///c4709ed1-bf88-4458-9e98-8e9b78150441) catalog view to return information about each server configuration option on the current server. The example returns the name (`name`) and description (`description`) of the option and whether the option is an advanced option (`is_advanced`).  
  
    ```wmimof  
    USE AdventureWorks2012;   
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;   
    GO  
  
    ```  
  
#### To change a server property by using sp_configure  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_configure](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8) to change a server property. The example changes the value of the `fill factor` option to `100`. The server must be restarted before the change can take effect.  
  
```tsql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 For more information, see [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md).  
  
##  <a name="PowerShellProcedure"></a> Using SQL Server Configuration Manager  
 Some server properties can be viewed or changed by using SQL Server Configuration Manager. For example, you can view the version and edition of the instance of SQL Server, or change the location where error log files are stored. These properties can also be viewed by querying the [Server-Related Dynamic Management Views and Functions](assetId:///d8f4e155-c2fb-4a1f-aa0d-e9790bdab925).  
  
#### To view or change server properties  
  
1.  On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Topics/TopicNameContainA/tokens/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
2.  In **SQL Server Configuration Manager**, click **SQL Server Services**.  
  
3.  In the details pane, right-click **SQL Server (<***instancename***>)**, and then click **Properties**.  
  
4.  In the **SQL Server (<***instancename***>) Properties** dialog box, change the server properties on the **Service** tab or the **Advanced** tab, and then click **OK**.  
  
##  <a name="FollowUp"></a> Follow Up: After you change server properties  
 For some properties, the server might have to be restarted before the change can take effect.  
  
## See Also  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [SET Statements (Transact-SQL)](assetId:///f7e107f8-0fcf-408b-b30f-da2323eeb714)   
 [SERVERPROPERTY (Transact-SQL)](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [SELECT (Transact-SQL)](assetId:///dc85caea-54d1-49af-b166-f3aa2f3a93d0)   
 [Configure WMI to Show Server Status in SQL Server Tools](assetId:///7e97197b-ed4d-40d1-9a52-9ab1d92401d7)   
 [SQL Server Configuration Manager](../../Topics/TopicNameNotContainA/SQL-Server-Configuration-Manager.md)   
 [Configuration Functions (Transact-SQL)](assetId:///066f15e7-3406-437e-93c4-3f247c529169)   
 [Server-Related Dynamic Management Views and Functions (Transact-SQL)](assetId:///d8f4e155-c2fb-4a1f-aa0d-e9790bdab925)