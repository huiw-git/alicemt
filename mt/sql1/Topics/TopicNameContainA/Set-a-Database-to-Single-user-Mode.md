---
title: "Set a Database to Single-user Mode"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# Set a Database to Single-user Mode
This topic describes how to set a user-defined database to single-user mode in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. Single-user mode specifies that only one user at a time can access the database and is generally used for maintenance actions.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To set a database to single-user mode, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If other users are connected to the database at the time that you set the database to single-user mode, their connections to the database will be closed without warning.  
  
-   The database remains in single-user mode even if the user that set the option logs off. At that point, a different user, but only one, can connect to the database.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Before you set the database to SINGLE_USER, verify that the AUTO_UPDATE_STATISTICS_ASYNC option is set to OFF. When this option is set to ON, the background thread that is used to update statistics takes a connection against the database, and you will be unable to access the database in single-user mode. For more information, see [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To set a database to single-user mode  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Right-click the database to change, and then click **Properties**.  
  
3.  In the **Database Properties** dialog box, click the **Options** page.  
  
4.  From the **Restrict Access** option, select **Single**.  
  
5.  If other users are connected to the database, an **Open Connections** message will appear. To change the property and close all other connections, click **Yes**.  
  
 You can also set the database to Multiple or Restricted access by using this procedure. For more information about the Restrict Access options, see [Database Properties (Options Page)](../../Topics/TopicNameNotContainA/Database-Properties--Options-Page-.md).  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To set a database to single-user mode  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example sets the database to `SINGLE_USER` mode to obtain exclusive access. The example then sets the state of the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database to `READ_ONLY` and returns access to the database to all users.The termination option `WITH ROLLBACK IMMEDIATE` is specified in the first `ALTER DATABASE` statement. This will cause all incomplete transactions to be rolled back and any other connections to the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database to be immediately disconnected.  
  
 [!CODE [DatabaseDDL#AlterDatabase8](../CodeSnippet/SQL15/tsql/databaseddl#alterdatabase8)]  
  
## See Also  
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)