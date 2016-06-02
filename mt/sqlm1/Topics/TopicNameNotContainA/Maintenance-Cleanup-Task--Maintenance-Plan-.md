---
title: Maintenance Cleanup Task (Maintenance Plan)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 022b679c-6799-4c13-9185-814224a20412
---
# Maintenance Cleanup Task (Maintenance Plan)
  Use the **Maintenance Cleanup Task** to remove old files related to maintenance plans, including text reports created by maintenance plans and database backup files.  
  
> [!NOTE]  
>  The Maintenance Cleanup task does not automatically delete files in the subfolders of the specified directory. This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files. If you want to delete files in first\-level subfolders, you must select **Include first\-level subfolders**.  
  
## Options  
 **Connection**  
 Displays the current connection.  
  
 **New**  
 Create a new server connection to use when performing this task. The **New Connection** dialog box is described below.  
  
 **Backup files**  
 Delete backup files.  
  
 **Maintenance Plan text reports**  
 Delete text reports of previously run maintenance plans.  
  
 **Delete specific file**  
 Delete the specific file provided in the **File name** box.  
  
 **File name**  
 Path and name of the file to be deleted.  
  
 **Search folder and delete files based on an extension**  
 Delete all files with the specified extension in the specified folder. Use this to delete multiple files at once, such as all backup files with the .bak extension, in the Tuesday folder.  
  
 **Folder**  
 Path and name of the folder containing the files to be deleted.  
  
 **File extension**  
 Provide the file extension of the files to be deleted.  
  
 **Include first\-level subfolders**  
 Delete files with the extension specified for **File extension** from first\-level subfolders under **Folder**.  
  
 **Delete files based on the age of the file at task run time**  
 Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.  
  
 **Delete files older than the following**  
 Specify the minimum age of the files that you want to delete by providing a number, and unit of time \(Day, Week, Month, or Year\). Files older than the time frame specified will be deleted.  
  
 **View T\-SQL**  
 View the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements performed against the server for this task, based on the selected options.  
  
> [!NOTE]  
>  When the number of objects affected is large, this display can take a considerable amount of time.  
  
## New Connection Dialog Box  
 **Connection name**  
 Enter a name for the new connection.  
  
 **Select or enter a server name**  
 Select a server to connect to when performing this task.  
  
 **…**  
 Select to view the list of available servers.  
  
 **Enter information to log on to the server**  
 Specify how to authenticate against the server.  
  
 **Use Windows integrated security**  
 Connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] with Microsoft Windows Authentication.  
  
 **Use a specific user name and password**  
 Connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] using SQL Server Authentication. This option is not available.  
  
 **User name**  
 Provide a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login to use when authenticating. This option is not available.  
  
 **Password**  
 Provide a password to use when authenticating. This option is not available.  
  
## See Also  
 [Maintenance Plans](../../Topics\TopicNameNotContainA/Maintenance-Plans.md)  
  
  