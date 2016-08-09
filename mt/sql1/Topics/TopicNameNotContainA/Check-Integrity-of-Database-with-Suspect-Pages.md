---
title: "Check Integrity of Database with Suspect Pages"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# Check Integrity of Database with Suspect Pages
This rule checks for user databases that have the database status set to suspect. When the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] reads a database page that contains an 824 error, the page is considered suspect, its page ID is recorded in the suspect_pages table in msdb, and the database that contains the page is set to suspect.  
  
 Error 824 indicates that a logical consistency error was detected during a read operation. This error frequently indicates data corruption caused by a faulty I/O subsystem component. This is a severe error condition that threatens database integrity and must be corrected immediately.  
  
## Best Practices Recommendations  
  
-   Review the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] error log for the details of the 824 error for this database.  
  
-   Complete a full database consistency check ([DBCC CHECKDB](assetId:///2c506167-0b69-49f7-9282-241e411910df)).  
  
-   Implement the user actions that are defined in [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397).  
  
## For More Information  
 [Manage the suspect_pages Table (SQL Server)](../../Topics/TopicNameNotContainA/Manage-the-suspect_pages-Table--SQL-Server-.md)