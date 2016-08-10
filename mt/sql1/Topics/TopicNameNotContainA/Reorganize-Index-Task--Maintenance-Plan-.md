---
title: "Reorganize Index Task (Maintenance Plan)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9cbebbd-f36f-4176-9832-382a46ac946c
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# Reorganize Index Task (Maintenance Plan)
Use the **ReorganizeIndex Task** dialog to move index pages into a more efficient search order. This task uses the `ALTER INDEX REORGANIZE` statement with [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] databases.  
  
## Options  
 **Connection**  
 Select the server connection to use when performing this task.  
  
 **New**  
 Create a new server connection to use when performing this task. The **New Connection** dialog box is described below.  
  
 **Databases**  
 Specify the databases affected by this task.  
  
-   **All databases**  
  
     Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases except tempdb.  
  
-   **All system databases**  
  
     Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] system databases except **tempdb**. No maintenance tasks are run against user-created databases.  
  
-   **All user databases**  
  
     Generate a maintenance plan that runs maintenance tasks against all user-created databases. No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] system databases.  
  
-   **These specific databases**  
  
     Generate a maintenance plan that runs maintenance tasks against only those databases that are selected. At least one database in the list must be selected if this option is chosen.  
  
 **Object**  
 Limit the **Selection** grid to display tables, views, or both.  
  
 **Selection**  
 Specify the tables or indexes affected by this task. Not available when **Tables and Views** is selected in the **Object** box.  
  
 **Compact large objects**  
 Deallocate space for tables and views when possible. This option uses `ALTER INDEX LOB_COMPACTION = ON`.  
  
 **View T-SQL**  
 View the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements performed against the server for this task, based on the selected options.  
  
> [!NOTE]  
>  When the number of objects affected is large, this display can take a considerable amount of time.  
  
## New Connection Dialog Box  
 **Connection name**  
 Enter a name for the new connection.  
  
 **Select or enter a server name**  
 Select a server to connect to when performing this task.  
  
 **Refresh**  
 Refresh the list of available servers.  
  
 **Enter information to log on to the server**  
 Specify how to authenticate against the server.  
  
 **Use Windows integrated security**  
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] with [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows Authentication.  
  
 **Use a specific user name and password**  
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication. This option is not available.  
  
 **User name**  
 Provide a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login to use when authenticating. This option is not available.  
  
 **Password**  
 Provide a password to use when authenticating. This option is not available.  
  
## See Also  
 [DBCC INDEXDEFRAG (Transact-SQL))](assetId:///b796c829-ef3a-405c-a784-48286d4fb2b9)   
 [DBCC INDEXDEFRAG (Transact-SQL)](assetId:///3c7df676-4843-44d0-8c1c-a9ab7e593b70)