---
title: "Database Properties (Filegroups Page)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
caps.latest.revision: 32
caps.handback.revision: 0
manager: jhubbard
---
# Database Properties (Filegroups Page)
Use this page to view the filegroups or add a new filegroup to the selected database. Filegroup types are separated into *row* filegroups, FILESTREAM data, and memory-optimized filegroups.  
  
 Row filegroups contain regular data and log files. FILESTREAM data filegroups contain FILESTREAM data files. These data files store information about how binary large object (BLOB) data is stored on the file system when you are using FILESTREAM storage. The options are the same for both types of filegroups.  
  
 If FILESTREAM is not enabled, the **Filestream** section will not be available. You can enable FILESTREAM storage by using [Server Properties (Advanced Page)](../../Topics/TopicNameNotContainA/Server-Properties--Advanced-Page-.md).  
  
 For information about how [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses row filegroups, see [Database Files and Filegroups](../../Topics/TopicNameNotContainA/Database-Files-and-Filegroups.md). For more information about FILESTREAM data and filegroups, see [FILESTREAM (SQL Server)](../../Topics/TopicNameNotContainA/FILESTREAM--SQL-Server-.md).  
  
 Memory-optimized file groups are required for a database to contain one or more memory-optimized tables.  
  
## Row and FILESTREAM Data Filegroup Options  
 **Name**  
 Enter the name of the filegroup.  
  
 **Files**  
 Displays the count of files in the filegroup.  
  
 **Read-only**  
 Select to set the filegroup to a read-only status.  
  
 **Default**  
 Select to make this filegroup the default filegroup. You can have one default filegroup for rows and one default filegroup for FILESTREAM data.  
  
 **Add**  
 Adds a new blank row to the grid listing filegroups for the database.  
  
 **Remove**  
 Removes the selected filegroup row from the grid.  
  
## Memory-Optimized Data Filegroup Options  
 **Name**  
 Enter the name of the memory-optimized filegroup.  
  
 **Filestream Files**  
 Displays the number of files (containers) in the memory-optimized data filegroup. You can add containers in the **Files** page.  
  
 **Add**  
 Adds a new blank row to the grid listing filegroups for the database.  
  
 **Remove**  
 Removes the selected filegroup row from the grid.  
  
## See Also  
 [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)   
 [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)