---
title: "Create Database (SQL Server Import and Export Wizard)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
caps.latest.revision: 41
caps.handback.revision: 0
manager: jhubbard
---
# Create Database (SQL Server Import and Export Wizard)
On the **Choose a Destination** page, if you select **New** to create a new destination database, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard shows the **Create Database** dialog box. On this page, you provide a name for the new database that the wizard will create. Optionally you can also change the settings for the initial size and the growth of the new database and its log file.  
  
> [!NOTE]  
>  If you're looking for info about the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] CREATE DATABASE statement, and not about this page of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard, see [CREATE DATABASE (SQL Server Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8).  
  
 This page offers only a subset of the options that are available for creating a new SQL Server database.  
  
-   For more info about the file size options on this page, see [CREATE DATABASE (SQL Server Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8).  
  
-   To see and configure all the options for a new [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database, use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics/TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Screen shot  
 The following screen shot shows the **Create Database** dialog box of the Wizard.  
  
 ![Create database page of the Import and Export Wizard](../../Topics/TopicNameNotContainA/images/Create-database.png "Create)  
  
## Options on this page  
  
> [!TIP]  
>  You have to provide a name for the new database on this page, but typically you can leave the other settings at their default values.  
  
 **Name**  
 Provide a unique name for the destination SQL Server database. Make sure that you follow SQL Server conventions when you name this database.  
  
-   The database name must be unique within an instance of SQL Server.  
  
-   The database name can be a maximum of 123 characters. (This allows 5 characters for the suffixes that SQL Server appends to the data file and the log file, within the maximum of 128 characters.)  
  
-   The database name must comply with the rules for identifiers in SQL Server. Here are the most important requirements.  
  
    -   The first character must be a letter, underscore (_), at sign (@), or number sign (#).  
  
    -   Subsequent characters can be letters, numbers, the at sign, dollar sign ($), number sign, or underscore.  
  
    -   You can't use spaces or other special characters.  
  
     For detailed info about these requirements, see [Database Identifiers](../../Topics/TopicNameNotContainA/Database-Identifiers.md).  
  
### Data file options  
 **Initial size**  
 Specify the number of megabytes for the initial size of the data file.  
  
 **No growth allowed**  
 Indicate whether the data file can grow beyond the specified initial size.  
  
 **Grow by percentage**  
 Specify a percentage by which the data file can grow.  
  
 **Grow by size**  
 Specify a number of megabytes by which the data file can grow.  
  
### Log file options  
 **Initial size**  
 Specify the number of megabytes for the initial size of the log file.  
  
 **No growth allowed**  
 Indicate whether the log file can grow beyond the specified initial size.  
  
 **Grow by percentage**  
 Specify a percentage by which the log file can grow.  
  
 **Grow by size**  
 Specify a number of megabytes by which the log file can grow.  
  
## What's next?  
 After you provide a name for the new database that the wizard will create and click **OK**, the **Create Database** dialog box returns you to the **Choose a Destination** page. For more info, see [Choose a Destination (SQL Server Import and Export Wizard)](../../Topics/TopicNameContainA/Choose-a-Destination--SQL-Server-Import-and-Export-Wizard-.md).