---
title: "Enable Stretch Database for a database"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37854256-8c99-4566-a552-432e3ea7c6da
caps.latest.revision: 64
manager: jhubbard
---
# Enable Stretch Database for a database
To configure a database for Stretch Database, select **Tasks &#124; Stretch &#124; Enable** for a database in SQL Server Management Studio to open the **Enable Database for Stretch** wizard. You can also use Transact-SQL to enable Stretch Database for a database.  
  
 If you select **Tasks &#124; Stretch &#124; Enable** for a table, and you have not yet enabled the database for Stretch Database, the wizard configures the database for Stretch Database and lets you configure tables as part of the process. Follow the steps in this topic instead of the steps in [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md).  
  
 Enabling Stretch Database on  a database or a table requires db_owner permissions. Enabling Stretch Database on a database also requires CONTROL DATABASE permissions.  
  
## Before you get started  
  
-   Before you configure a database for Stretch, we recommend that you run the Stretch Database Advisor to identify databases and tables that are eligible for Stretch. The Stretch Database Advisor also identifies blocking issues. For more info, see [Identify databases and tables for Stretch Database by running Stretch Database Advisor](../../Topics/TopicNameNotContainA/Identify-databases-and-tables-for-Stretch-Database-by-running-Stretch-Database-Advisor.md).  
  
-   Review [Limitations for Stretch Database](../../Topics/TopicNameNotContainA/Limitations-for-Stretch-Database.md). Also review [Frequently asked questions about Stretch Database](../../Topics/TopicNameNotContainA/Stretch-Database.md#FAQ).  
  
-   Stretch Database migrates data to Azure . Therefore you have to have an Azure account and a subscription for billing. To get an Azure account, [click here](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
-   Have the info you need to create a new remote database or to select an existing remote database, and to create a firewall rule that lets your local server communicate with the remote server.  
  
##  <a name="EnableTSQLServer"></a> Prerequisite: Permission to enable Stretch Database on the server  
 Before you can enable Stretch Database on a database or a table, you have to enable it on the local server. This operation requires sysadmin or serveradmin permissions.  
  
-   If you have the required administrative permissions, the **Enable Database for Stretch** wizard configures the server for Stretch .  
  
-   If you don't have the required permissions,  an administrator has to enable the option manually by running **sp_configure** before you run the wizard, or an administrator has to run the wizard.  
  
 To enable Stretch Database on the server manually, run **sp_configure** and turn on the **remote data archive** option. The following example enables the **remote data archive** option by setting its value to 1.  
  
```  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 For more info, see [Configure the remote data archive Server Configuration Option](../../Topics/TopicNameNotContainA/Configure-the-remote-data-archive-Server-Configuration-Option.md) and [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8).  
  
##  <a name="Wizard"></a> Use the wizard to enable Stretch Database on a database  
 For info about the Enable Database for Stretch Wizard, including the info that you have to enter and the choices that you have to make, see [Get started by running the Enable Database for Stretch Wizard](../../Topics/TopicNameNotContainA/Get-started-by-running-the-Enable-Database-for-Stretch-Wizard.md).  
  
##  <a name="EnableTSQLDatabase"></a> Use Transact-SQL to enable Stretch Database on a database  
 Before you can enable Stretch Database on individual tables, you have to enable it on the database.  
  
 Enabling Stretch Database on  a database or a table requires db_owner permissions. Enabling Stretch Database on a database also requires CONTROL DATABASE permissions.  
  
1.  Before you begin, choose an existing Azure server for the data that Stretch Database migrates, or create a new server.  
  
2.  On the Azure server, create a firewall rule with the IP address (or IP address range) of the  SQL Server that lets SQL Server communicate with the remote server.  
  
3.  To configure a SQL Server database for Stretch Database, the database has to have a database master key. The database master key secures the credentials that Stretch Database uses to connect to the remote database. To create the database master key manually, see [CREATE MASTER KEY (Transact-SQL)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76) and [Create a Database Master Key](../../Topics/TopicNameContainA/Create-a-Database-Master-Key.md).  
  
    ```tsql  
    USE <database>  
    GO  
  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD='<password>'  
  
    ```  
  
4.  When you configure a database for Stretch Database, you have to provide a credential for Stretch Database to use for communication between the on premises SQL Server and the remote Azure server. You have two options.  
  
    -   You can  provide an administrator credential.  
  
        -   If you enable Stretch Database by running the wizard, you can create the credential at that time.  
  
        -   If you enable Stretch Database by running **ALTER DATABASE**, you have to create the credential manually before you enable Stretch Database.  
  
         To create the credential manually, see [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045). Creating the credential requires ALTER ANY CREDENTIAL permissions.  
  
        ```tsql  
        CREATE DATABASE SCOPED CREDENTIAL <db_scoped_credential_name>  
            WITH IDENTITY = '<identity>' , SECRET = '<secret>'  
        GO  
  
        ```  
  
    -   You can use a federated service account for the SQL Server to communicate with the remote Azure server when the following conditions are all true.  
  
        -   The service account under which the instance of SQL Server is running is a domain account.  
  
        -   The domain account belongs to a domain whose Active Directory is federated with Azure Active Directory.  
  
        -   The remote Azure server is configured to support Azure Active Directory authentication.  
  
        -   The service account under which the instance of SQL Server is running must be configured as a dbmanager or sysadmin account on the remote Azure server.  
  
5.  To configure a database for Stretch Database, run the ALTER DATABASE command.  
  
    1.  For the SERVER argument, provide the name of an existing Azure server, including the `.database.windows.net` portion of the name - for example, `MyStretchDatabaseServer.database.windows.net`.  
  
    2.  Provide an existing administrator credential with the CREDENTIAL argument, or specify FEDERATED_SERVICE_ACCOUNT = ON. The following example provides an existing credential.  
  
    ```tsql  
    ALTER DATABASE <database name>  
        SET REMOTE_DATA_ARCHIVE = ON  
            (  
                SERVER = '<server_name>' ,  
                CREDENTIAL = <db_scoped_credential_name>  
            ) ;  
    GO;  
    ```  
  
## Next steps  
 Enable additional tables for Stretch Database. Monitor data migration and manage Stretch-enabled databases and tables.  
  
-   [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md) to enable additional tables.  
  
-   [Monitor and troubleshoot data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Monitor-and-troubleshoot-data-migration--Stretch-Database-.md) to see the status of data migration.  
  
-   [Pause and resume data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Pause-and-resume-data-migration--Stretch-Database-.md)  
  
-   [Manage and troubleshoot Stretch Database](../../Topics/TopicNameNotContainA/Manage-and-troubleshoot-Stretch-Database.md)  
  
-   [Backup Stretch-enabled databases (Stretch Database)](../../Topics/TopicNameNotContainA/Backup-Stretch-enabled-databases--Stretch-Database-.md)  
  
## See Also  
 [Identify databases and tables for Stretch Database by running Stretch Database Advisor](../../Topics/TopicNameNotContainA/Identify-databases-and-tables-for-Stretch-Database-by-running-Stretch-Database-Advisor.md)   
 [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc)