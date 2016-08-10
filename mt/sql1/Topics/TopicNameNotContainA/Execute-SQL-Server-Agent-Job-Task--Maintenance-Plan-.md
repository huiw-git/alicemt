---
title: "Execute SQL Server Agent Job Task (Maintenance Plan)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
caps.latest.revision: 22
caps.handback.revision: 0
manager: jhubbard
---
# Execute SQL Server Agent Job Task (Maintenance Plan)
Use the **Execute SQL Server Agent Job Task** dialog to execute Microsoft SQL Server Agent jobs within a maintenance plan. This option will not be available if you have no SQL Server Agent jobs on the selected connection.  
  
 This task uses the **.sp_start_job** statement.  
  
## UIElement List  
 **Connection**  
 Select the server connection to use when performing this task.  
  
 **New**  
 Create a new server connection to use when performing this task. The **New Connection** dialog box is described below.  
  
 **Available SQL Agent jobs**  
 Select the job to execute. The grid provides the **Job name** and **Description** to identify the jobs.  
  
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
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] with Microsoft Windows Authentication.  
  
 **Use a specific user name and password**  
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication. This option is not available.  
  
 **User name**  
 Provide a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login to use when authenticating. This option is not available.  
  
 **Password**  
 Provide a password to use when authenticating. This option is not available.  
  
## See Also  
 [sp_start_job (Transact-SQL)](assetId:///6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274)   
 [Create a Job](assetId:///b35af2b6-6594-40d1-9861-4d5dd906048c)   
 [sp_start_job (Transact-SQL)](assetId:///8a91df6a-eb84-4512-9a17-4a6e32a9538a)