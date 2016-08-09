---
title: "History Cleanup Task (Maintenance Plan)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
caps.latest.revision: 22
caps.handback.revision: 0
manager: jhubbard
---
# History Cleanup Task (Maintenance Plan)
Use the **History Cleanup Task** dialog to discard old historical information from tables in the msdb database. This task supports deleting backup and restore history, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent Job history, and maintenance plan history.  
  
 This statement uses the **sp_purge_jobhistory** and **sp_delete_backuphistory** statements.  
  
## UIElement List  
 **Connection**  
 Select the server connection to use when performing this task.  
  
 **New**  
 Create a new server connection to use when performing this task. The **New Connection** dialog box is described later in this topic.  
  
 **Backup and restore history**  
 Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] create a recovery plan when you want to restore a database. The retention period should be at least the frequency of full database back ups.  
  
 **SQL Server Agent Job history**  
 This history can help you troubleshoot failed jobs, or determine why database actions occurred.  
  
 **Maintenance plan history**  
 This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.  
  
 **Remove historical data older than**  
 Specify age of items that you want to delete.  
  
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
 Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] with Microsoft Windows Authentication.  
  
 **Use a specific user name and password**  
 Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] using SQL Server Authentication. This option is not available.  
  
 **User name**  
 Provide a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login to use when authenticating. This option is not available.  
  
 **Password**  
 Provide a password to use when authenticating. This option is not available.  
  
## See Also  
 [sp_delete_backuphistory (Transact-SQL)](assetId:///237f9bad-636d-4262-9bfb-66c034a43e88)   
 [sp_delete_backuphistory (Transact-SQL)](assetId:///bdb56834-616e-47e4-b942-e895d2325e97)