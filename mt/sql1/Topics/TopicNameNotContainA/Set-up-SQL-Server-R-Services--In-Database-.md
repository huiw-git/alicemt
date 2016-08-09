---
title: "Set up SQL Server R Services (In-Database)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 20
manager: paulettm
---
# Set up SQL Server R Services (In-Database)
In [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], you can now install all components related to [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] by using the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup wizard.  
  
 After setup is complete, there are some additional steps required to give users permissions to specific databases. If you experience problems with database access, or need to enable execution of R on the instance using remote compute contexts, see [Additional Configuration Steps](#bkmk_Additional), as well as [Upgrade and Installation FAQ (SQL Server R Services)](../../Topics/TopicNameNotContainA/Upgrade-and-Installation-FAQ--SQL-Server-R-Services-.md).  
  
##  <a name="bkmk_installRServicesInDatabase"></a> Install R Services (In-Database) on SQL Server 2016 RC2 and RC3  
 For information about how to do unattended installs, see [Unattended Installs of SQL Server R Services](../../Topics/TopicNameNotContainA/Unattended-Installs-of-SQL-Server-R-Services.md).  
  
1.  Run [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup.  
  
2.  On the **Installation** tab, click **New SQL Server stand-alone installation or add features to an existing installation**.  
  
    > [!NOTE]  
    >  You cannot install [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] on a failover cluster. However, you can install [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] on a standalone computer that uses Always On and is part of an availability group. For more information about using R Services in an Always On availability group, see [Always On Availability Groups: Interoperability (SQL Server)](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md).  
  
3.  On the **Feature Selection** page, select these options:  
  
    -   **Database Engine Services**  
  
         At least one instance of the database engine is required to use [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)]. You can use either a default or named instance.  
  
    -   **R Services (In-Database)**  
  
         This option configures the database services used by R jobs and installs the extensions that support external scripts and processes.  
  
         enable  
  
         This option is required when installing on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] computer.  
  
4.  On the page, **Consent to Install Microsoft R Open**, click **Accept**.  
  
     This license agreement is required to download Microsoft R Open, which include a distribution of the open source R base packages and tools, together with enhanced R packages and connectivity providers from Revolution Analytics.  
  
    > [!NOTE]  
    >  If the computer you are using does not have Internet access, you can pause setup at this point to download the installers separately as described here: [Installing R Components without Internet Access](../../Topics/TopicNameNotContainA/Installing-R-Components-without-Internet-Access.md)  
  
     Click **Accept**, wait until the **Next** button becomes active, and then click **Next**.  
  
5.  On the **Ready to Install** page, verify that these selections are included, and click **Install**.  
  
     **Features**  
  
     Database Engine Services  
  
     R Services (In-Database)  
  
6.  When installation is complete, you should see a list of components.  
  
     You should also see the following message, indicating that a restart is required:  One or more affected files have operations pending. You must restart your computer after the setup process is completed.  
  
7.  Before restarting, in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], run the following command to enable the feature.  
  
    ```  
    Exec sp_configure  'external scripts enabled', 1  
    Reconfigure  with  override  
  
    ```  
  
    > [!NOTE]  
    >  You must explicitly enable the engine feature; otherwise, it will not be possible to invoke R scripts even if the feature has been installed configured by setup.  
  
8.  Restart the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance. This will automatically restart the related [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] service as well.  
  
 Optionally, you can now proceed to install the R tools on a different computer that will be used for data science development. For more information, see [Create a Standalone R Server](../../Topics/TopicNameContainA/Create-a-Standalone-R-Server.md).  
  
## Verify That R is Running  
 In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], open a new **Query** window and run a simple test script such as the following to verify that the R runtime can be called.  
  
```  
exec sp_execute_external_script  @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',    
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go  
```  
  
 Expected Results  
  
 **hello**  
**1**   
##  <a name="bkmk_Additional"></a> Additional Configuration Steps  
 All services required to run R are configured by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup, and you no longer need to run a script to register the R components. However, there are some additional steps to take if you need to run R commands from a remote data science client.  
  
-   **Create a login on the instance for the Windows group used by the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)]**  
  
     By default, setup of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] creates a new Windows user group that contains accounts used for running all R processes on the instance. (For more information, see [Modify the User Account Pool for SQL Server R Services](../../Topics/TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md).)  
  
     If you need to run R jobs from a remote data science client, or if you need to embed ODBC calls in your R code, this group must have **Connect** permissions to the instance in which [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] has been enabled.  
  
     For example, on a named instance, the database administrator might run a statement like the following, in the context of the master database:  
  
    ```  
  
    CREATE LOGIN [MyServer\SQLRUserGroupMyNamedInstance] FROM WINDOWS WITH DEFAULT_DATABASE=[master]  
    ```  
  
     This would give the group account that was created for R on the named instance the permissions necessary  to run R jobs through the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)].  
  
-   **Give the user permissions to run R script in each working database**  
  
     All [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements are executed in the context of a database. If the login or user account that you use for running R scripts does not have a default database, you must connect explicitly to the database before creating a query that contains R code. Moreover, that user must have permissions to run R script in that database.  
  
    ```  
    GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]  
    ```  
  
     For sysadmin, this permission is implicit.  
  
-   **Give the user read, write, or DDL permissions as needed in additional databases**  
  
     While running R scripts, the user account may need to read data from other databases, create new tables to store results, and write data into tables. Therefore, for each user who will be executing R scripts, be sure that the user account has **db_datareader**, **db_datawriter**, or **db_ddladmin** permissions on the specific database. For example, the following [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement gives the existing user RSQLUser01 the rights to create new tables in the IrisTest database.  
  
    ```  
    use IrisTest  
    GO  
    EXEC sp_addrolemember 'db_datareader', 'RSQLUser01'  
    ```  
  
     For more information about the permissions included in each role, see [Database-Level Roles](../../Topics/TopicNameNotContainA/Database-Level-Roles.md).  
  
-   **Set up the R components on a client computer for R script development**  
  
     [Create a Standalone R Server](../../Topics/TopicNameContainA/Create-a-Standalone-R-Server.md)  
  
     Currently this package includes only the Microsoft R Open tools and packages, and does not include an R development environment.  
  
-   **Create an ODBC data source for the instance on your data science client**  
  
     If you create an R solution on a data science client computer and need to connect to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] computer as the compute context, you can use either a SQL login, or integrated Windows authentication.  
  
     If you use a SQL login, ensure that the login has appropriate permissions on the database where you will be reading data (Connect and SELECT permissions, or add the login to the db_datareader role). If you need to create objects, you will need DDL admin rights.  To save data to tables, the login to the db_datawriter role.  
  
     If you use Windows authentication, you must configure an ODBC data source on the data science client that specifies that instance name and other connection information.  
  
     [Using the ODBC Data Source Administrator](http://windows.microsoft.com/windows/using-odbc-data-source-administrator)  
  
## Optimizing the Server for R  
 The default settings for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup are intended to optimize the balance of the server for a variety of services supported by the database engine, which might include  ETL processes, reporting, auditing, and applications that use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data. Therefore, under the default settings you  might find resources for R operations restricted or throttled, particularly in memory-intensive operations.  
  
 To ensure that R tasks are prioritized and resourced appropriately, we recommend that you use Resource Governor to configure an external resource pool specific for R operation. You might also wish to change the amount of memory allocated to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database engine, or increase the number of accounts running under the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] service.  
  
-   Configure a resource pool for managing external resources  
  
     [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](assetId:///8cc798ad-c395-461c-b7ff-8c561c098808)  
  
-   Change the amount of memory reserved for the database engine  
  
     [Server Memory Server Configuration Options](../../Topics/TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md)  
  
-   Change the number of R accounts that can be started by [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)]  
  
     [Modify the User Account Pool for SQL Server R Services](../../Topics/TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md)  
  
## Get the R Source Code (Optional)  
 [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] includes a distribution of the open source R base packages.  
  
 Optionally, click one of these links to immediately begin downloading the modified GPL/LGPL source code. This is made available in compliance with the GNU General Public License, but is not required to install or use [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)].  
  
-   Compatible with RC2 ([.tar archive](http://go.microsoft.com/fwlink/?LinkId=786770))  
  
-   Compatible with RC3 ([.tar archive](http://go.microsoft.com/fwlink/?LinkId=786771))  
  
## Troubleshooting  
 Run into trouble? See this list of common issues when installing pre-release versions of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)]  
  
 [Upgrade and Installation FAQ (SQL Server R Services)](../../Topics/TopicNameNotContainA/Upgrade-and-Installation-FAQ--SQL-Server-R-Services-.md)  
  
## See Also  
 [Set Up  a Data Science Client](../../Topics/TopicNameContainA/Set-Up--a-Data-Science-Client.md)   
 [Create a Standalone R Server](../../Topics/TopicNameContainA/Create-a-Standalone-R-Server.md)