---
title: Stretch 4 enable database
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8af4c5f-fac4-49c6-933c-776ed21d99f7
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Stretch 4 enable database
To configure a database for Stretch Database, select **Tasks &#124; Stretch &#124; Enable** for a database in SQL Server Management Studio to open the **Enable Database for Stretch** wizard. You can also use Transact\-SQL to enable Stretch Database for a database.  
  
 If you select **Tasks &#124; Stretch &#124; Enable** for a table, and you have not yet enabled the database for Stretch Database, the wizard configures the database for Stretch Database and lets you configure tables as part of the process. Follow the steps in this topic instead of the steps in [Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc).  
  
 Enabling Stretch Database on  a database or a table requires db\_owner permissions. Enabling Stretch Database on a database also requires CONTROL DATABASE permissions.  
  
## Before you get started  
  
-   Before you configure a database for Stretch, we recommend that you run the Stretch Database Advisor to identify databases and tables that are eligible for Stretch. The Stretch Database Advisor also identifies blocking issues. For more info, see [Identify databases and tables for Stretch Database](assetId:///81bd93d8-eef8-4572-88d7-5c37ab5ac2bf).  
  
-   Review [Surface area limitations and blocking issues for Stretch Database](assetId:///2b1fbec1-7859-44fc-8417-724fc57a59c0). Also review [Frequently asked questions about Stretch Database](assetId:///ce6db775-21a5-40bc-95a1-f560376d4ee2#FAQ).  
  
-   Stretch Database migrates data to Azure . Therefore you have to have an Azure account and a subscription for billing. To get an Azure account, [click here](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
-   Have the info you need to create a new remote database or to select an existing remote database, and to create a firewall rule that lets your local server communicate with the remote server.  
  
##  <a name="EnableTSQLServer"></a> Prerequisite: Permission to enable Stretch Database on the server  
 Before you can enable Stretch Database on a database or a table, you have to enable it on the local server. This operation requires sysadmin or serveradmin permissions.  
  
-   If you have the required administrative permissions, the **Enable Database for Stretch** wizard configures the server for Stretch .  
  
-   If you don't have the required permissions,  an administrator has to enable the option manually by running **sp\_configure** before you run the wizard, or an administrator has to run the wizard.  
  
 To enable Stretch Database on the server manually, run **sp\_configure** and turn on the **remote data archive** option. The following example enables the **remote data archive** option by setting its value to 1.  
  
```  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 For more info, see [Configure the remote data archive Server Configuration Option](assetId:///b5817b5a-f39a-4faf-b11e-a47b54fd9f32) and [sp\_configure \(Transact\-SQL\)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8).  
  
##  <a name="Wizard"></a> Use the wizard to enable Stretch Database on a database  
 For info about the Enable Database for Stretch Wizard, including the info that you have to enter and the choices that you have to make, see [Enable Database for Stretch Wizard](assetId:///855dd9fc-f80c-4dbc-bf46-55a9736bfe15).  
  
##  <a name="EnableTSQLDatabase"></a> Use Transact\-SQL to enable Stretch Database on a database  
 Before you can enable Stretch Database on individual tables, you have to enable it on the database.  
  
 Enabling Stretch Database on  a database or a table requires db\_owner permissions. Enabling Stretch Database on a database also requires CONTROL DATABASE permissions.  
  
1.  Before you begin, choose an existing Azure server for the data that Stretch Database migrates, or create a new server.  
  
2.  On the Azure server, create a firewall rule with the IP address \(or IP address range\) of the  SQL Server that lets SQL Server communicate with the remote server.  
  
3.  To configure a SQL Server database for Stretch Database, the database has to have a database master key. The database master key secures the credentials that Stretch Database uses to connect to the remote database. To create the database master key manually, see [CREATE MASTER KEY \(Transact\-SQL\)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76) and [Create a Database Master Key](assetId:///8cb24263-e97d-4e4d-9429-6cf494a4d5eb).  
  
    ```tsql  
    USE <database>  
    GO  
  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD='<password>'  
  
    ```  
  
4.  When you configure a database for Stretch Database, you have to provide a credential for Stretch Database to use for communication between the on premises SQL Server and the remote Azure server. You have two options.  
  
    -   You can  provide an administrator credential.  
  
        -   If you enable Stretch Database by running the wizard, you can create the credential at that time.  
  
        -   If you enable Stretch Database by running **ALTER DATABASE**, you have to create the credential manually before you enable Stretch Database.  
  
         To create the credential manually, see [CREATE DATABASE SCOPED CREDENTIAL \(Transact\-SQL\)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045). Creating the credential requires ALTER ANY CREDENTIAL permissions.  
  
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
  
    1.  For the SERVER argument, provide the name of an existing Azure server, including the `.database.windows.net` portion of the name \- for example, `MyStretchDatabaseServer.database.windows.net`.  
  
    2.  Provide an existing administrator credential with the CREDENTIAL argument, or specify FEDERATED\_SERVICE\_ACCOUNT \= ON. The following example provides an existing credential.  
  
    ```tsql  
    ALTER DATABASE <database name>  
        SET REMOTE_DATA_ARCHIVE = ON  
            (  
                SERVER = <server_name> ,  
                CREDENTIAL = <db_scoped_credential_name>  
            ) ;  
    GO;  
    ```  
  
## Next steps  
 Enable additional tables for Stretch Database. Monitor data migration and manage Stretch\-enabled databases and tables.  
  
-   [Enable Stretch Database for a table](assetId:///de4ac0c5-46ef-4593-a11e-9dd9bcd3ccdc) to enable additional tables.  
  
-   [Monitor Stretch Database](assetId:///06950858-8c02-4ec6-9c59-42b787316a2d) to see the status of data migration.  
  
-   [Pause and resume Stretch Database](assetId:///65d6a990-b295-41b2-97f9-7b6bf3000e4d)  
  
-   [Manage and troubleshoot Stretch Database](assetId:///6334db3e-9297-44df-8d53-211187a95520)  
  
-   [Backup and restore Stretch\-enabled databases](assetId:///18f0dff0-d8ce-4bee-a935-76ed6dfb3208)  
  
## See Also  
 [Identify databases and tables for Stretch Database](assetId:///81bd93d8-eef8-4572-88d7-5c37ab5ac2bf)   
 [ALTER DATABASE SET Options \(Transact\-SQL\)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc)   
 [ALTER TABLE \(Transact\-SQL\)](assetId:///f1745145-182d-4301-a334-18f799d361d1)