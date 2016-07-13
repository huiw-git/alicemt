---
title: Installing SSMA for MySQL Client (MySQLToSQL)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
manager:lonnyb
---
# Installing SSMA for MySQL Client (MySQLToSQL)
The SSMA for MySQL client consists of the program files that perform the following tasks:  
  
-   Connect to a MySQL database.  
  
-   Connect to an instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure.  
  
-   Convert the MySQL database objects to the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure objects.  
  
-   Load the objects into [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure.  
  
-   Migrate data to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure.  
  
This topic provides the installation prerequisites and instructions for installing SSMA for MySQL client.  
  
## Prerequisites  
SSMA for MySQL is designed to work with MySQL 4.1 or later versions and all editions of SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016 and Azure SQL DB.  
  
Before you install SSMA, make sure that the computer meets the following requirements:  
  
-   Windows 7 or later versions, or Windows Server 2008 or later versions.  
  
-   [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Installer 3.1 or a later version.  
  
-   The [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[dnprdnshort](../content/includes/dnprdnshort_md.md)] version 4.0 or a later version. The [!INCLUDE[dnprdnshort](../content/includes/dnprdnshort_md.md)] version 4.0 is available on the SQL Server product media. You can also obtain it from the [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   MySQL ODBC 5.1 Driver and connectivity to the MySQL databases that you want to migrate. You can install the MySQL from the MySQL Web site. For information about connectivity, see [Connecting to MySQL &#40;MySQLToSQL&#41;](../content/Connecting-to-MySQL--MySQLToSQL-.md)  
  
-   Access to and sufficient permissions on the computer that hosts the target instance of SQL Server where you will be migrating database objects and data. For more information, see [Connecting to SQL Server &#40;MySQLToSQL&#41;](../content/Connecting-to-SQL-Server--MySQLToSQL-.md)  
  
-   In case of SQL Azure projects, Access to and sufficient permissions to the instance of Azure SQL DB where you will be migrating database objects and data. For more information, see [Connecting to Azure SQL DB &#40;MySQLToSQL&#41;](../content/Connecting-to-Azure-SQL-DB--MySQLToSQL-.md).  
  
-   4 GB RAM recommended.  
  
## Installing SSMA for MySQL Client  
SSMA is a Web download. To download the latest version, see the [SQL Server Migration Assistant download page](http://aka.ms/ssmaformysql).  
  
After you download the latest version, you must extract the installation files before you can install SSMA.  
  
**To install the SSMA client**  
  
1.  Double\-click SSMA for MySQL *n*.Install.exe, where *n* is the build number.  
  
2.  On the Welcome page, click **Next**.  
  
    If you do not have the prerequisites installed, a message will appear indicating that you must first install the required components. Make sure that you have installed all the prerequisites before running the installation program again.  
  
3.  Read the End User License Agreement. If you agree, select **I accept the terms in the license agreement**, and then click **Next**.  
  
4.  On the Choose Setup Type page, click **Typical**.  
  
5.  Click **Install**.  
  
> [!IMPORTANT]  
> 1.  Please uninstall all prior versions of SSMA for MySQL before installing the new version.  
  
The default installation location is C:\\Program Files\\Microsoft SQL Server Migration Assistant for MySQL.  
  
On 64\-bit Windows machine the product is installed in C:\\Microsoft SQL Server Migration Assistant for MySQL.  
  
## See Also  
[Migrating MySQL Databases to SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../content/Migrating-MySQL-Databases-to-SQL-Server---Azure-SQL-DB--MySQLToSql-.md)  
  
