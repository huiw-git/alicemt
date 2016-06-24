---
title: Check Integrity of Database with Suspect Pages
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
---
# Check Integrity of Database with Suspect Pages
  This rule checks for user databases that have the database status set to suspect. When the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/includes/ssDEnoversion_md.md)] reads a database page that contains an 824 error, the page is considered suspect, its page ID is recorded in the suspect_pages table in msdb, and the database that contains the page is set to suspect.  
  
 Error 824 indicates that a logical consistency error was detected during a read operation. This error frequently indicates data corruption caused by a faulty I/O subsystem component. This is a severe error condition that threatens database integrity and must be corrected immediately.  
  
## Best Practices Recommendations  
  
-   Review the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] error log for the details of the 824 error for this database.  
  
-   Complete a full database consistency check ([DBCC CHECKDB](../Topic/DBCC%20CHECKDB%20\(Transact-SQL\).md)).  
  
-   Implement the user actions that are defined in [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397).  
  
## For More Information  
 [Manage the suspect_pages Table &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Manage-the-suspect_pages-Table--SQL-Server-.md)  
  
  