---
title: Set up SQL Server R Services (In-Database)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
---
# Set up SQL Server R Services (In-Database)
  In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you can now install all components related to [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup wizard.  
  
 After setup is complete, there are some additional steps required to enable R Services feature, to configure accounts, and give users permissions to specific databases.   
  
If you experience problems with database access after completing setup, or need to uninstall previous versions,  [Upgrade and Installation FAQ &#40;SQL Server R Services&#41;](../Topic/Upgrade%20and%20Installation%20FAQ%20\(SQL%20Server%20R%20Services\).md).  
  
##  <a name="bkmk_installRServicesInDatabase"></a> Step 1: Install R Services \(In\-Database\) on SQL Server 2016  
   
  
1.  Run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup.  
  
    For information about how to do unattended installs, see [Unattended Installs of SQL Server R Services](../../Topics\TopicNameNotContainA/Unattended-Installs-of-SQL-Server-R-Services.md).  
  
2.  On the **Installation** tab, click **New SQL Server stand\-alone installation or add features to an existing installation**.  
  
    > [!NOTE]  
    >  You cannot install [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] on a failover cluster. However, you can install [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] on a standalone computer that uses Always On and is part of an availability group. For more information about using R Services in an Always On availability group, see [Always On Availability Groups: Interoperability](Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md).  
  
3.  On the **Feature Selection** page, select these options:  
  
    -   **Database Engine Services**  
  
         At least one instance of the database engine is required to use [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]. You can use either a default or named instance.  
  
    -   **R Services \(In\-Database\)**  
  
         This option configures the database services used by R jobs and installs the extensions that support external scripts and processes.  
  
  
4.  On the page, **Consent to Install Microsoft R Open**, click **Accept**.  
  
     This license agreement is required to download Microsoft R Open, which include a distribution of the open source R base packages and tools, together with enhanced R packages and connectivity providers from Revolution Analytics.  
  
    > [!NOTE]  
    >  If the computer you are using does not have Internet access, you can pause setup at this point to download the installers separately as described here: [Installing R Components without Internet Access](../../Topics\TopicNameNotContainA/Installing-R-Components-without-Internet-Access.md)  
  
     Click **Accept**, wait until the **Next** button becomes active, and then click **Next**.  
  
5.  On the **Ready to Install** page, verify that these selections are included, and click **Install**.  
  
     **Features**  
  
     Database Engine Services  
  
     R Services \(In\-Database\)  
  
6.  When installation is complete, restart the computer.   
  
  
##  <a name="bkmk_enableFeature"></a> Step 2: Enable R Service and Verify that Local R Script Execution Works  
  
  
1. Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. If it is not already installed, you can rerun the SQL Server setup wizard to open a download link and install it.  
  
2. Connect to the instance where you installed R Services (In-Database), and run the following command to explicitly enable the R Services feature; otherwise, it will not be possible to invoke R scripts even if the feature has been installed by setup.  
  
   ~~~~  
  
   Exec sp_configure  'external scripts enabled', 1  
   Reconfigure  with  override  
  
   ~~~~  
  
10. Restart the SQL Server service for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. This will automatically restart the related [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service as well. You can restart the service using the Services panel in Control Panel, or by using SQL Server Configuration Manager.  
  
9. After the SQL Server service is avaialble, verify  that the R feature is enabled by running the following command and checking that the *run_value* is set to 1:  
  
    ~~~~  
  
   Exec sp_configure  'external scripts enabled'  
  
    ~~~~  
  
10. At this point you should be able to run simple R scripts like the following in  [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]:  
  
    ~~~~  
    exec sp_execute_external_script  @language =N'R',  
    @script=N'OutputDataSet<-InputDataSet',    
    @input_data_1 =N'select 1 as hello'  
    with result sets (([hello] int not null));  
    go  
    ~~~~  
  
 Expected Results  
  
 **hello**  
**1**   
  
  However, some additional steps are required if you need to access SQL Server data, or run R commands from a remote data science client.  
  
##  <a name="bkmk_configureAccounts"></a> Step 3: Enable Implied Authentication for Launchpad Accounts  
   
  
During setup, 20 new Windows user accounts are created for the purpose of running tasks under the security token of the [!INCLUDE[rsql_launchpad_md](../../Token\Other/rsql_launchpad_md.md)] service. You can view these accounts in the Windows user group, **SQLRUserGroup**.    
  
However, if you need to run R scripts from a remote data science client and are using Windows authentication, these worker accounts must be given permission to log into the SQL Server instance on your behalf.  
  
1. In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], in Object Explorer, expand **Security**, right-click **Logins**, and select **New Login**.  
2. In the **Login - New** dialog box, click **Search**.  
3. Click **Object Types** and select **Groups**. Deselect everything else.  
4. In Enter the object name to select, type *SQLRUserGroup*  and click **Check Names**.  
5. The name of the local group associated with the instance's Launchpad service should resolve to something like *instancename\SQLRUserGroup*. Click **OK**.  
6. By default, the login is assigned to the **public** role and has permission to connect to the database engine. 
7. Click **OK**.  
  
> [!NOTE]
>
>  When a user sends an R script from an external client, SQL Server will activate an available worker account, map it to the identity of the calling user, and run the R script on behalf of the user. This is a new service of the database engine that supports secure execution of external scripts, called *implied authentication*. If you use a SQL login, this extra step is not required.  
  
  
## Step 4: Give Non-Admin Users R Script Permissions  
  
If you installed SQL Server yourself and are running R scripts in your own instance, you are typically executing scripts as **sysadmin** and thus have implicit permission over various operations and all data in the database, as well as the ability to install new R package as needed.  
  
However, in an enterprise scenario, most users (or SQL logins) do not have such elevated permissions. Therefore, for each user that will be running external scripts, you must grant the user permissions to run R script in each database where R will be used.   
  
  
~~~~  
USE <database_name>  
GO  
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]  
~~~~  
  
   
  
  
##  <a name="bkmk_Additional"></a> Additional Configuration Steps  
  
  
-   **Modify the number of worker accounts used by [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)]**, their names, and passwords  
  
     If you think you will use R heavily, or have many concurrent users running scripts, you can increase the number of worker accounts that are assigned to the Launchpad service for running R scripts on the instance. \(For more information, see [Modify the User Account Pool for SQL Server R Services](../../Topics\TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md).\)  
  
  
-   **Give your R users or logins read, write, or DDL permissions as needed in additional databases**  
  
     While running R scripts, the user account may need to read data from other databases, create new tables to store results, and write data into tables. Therefore, for each user who will be executing R scripts, be sure that the user account has **db\_datareader**, **db\_datawriter**, or **db\_ddladmin** permissions on the specific database.   
       
     For example, the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement gives the SQL login *MySQLLogin* the rights to run SQL queries in the *RSamples* database. To run this statement, the SQL login must already exist in the security context of the server.  
  
    ```  
    USE RSamples  
    GO  
    EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'  
    ```  
  
     For more information about the permissions included in each role, see [Database-Level Roles](../../Topics\TopicNameNotContainA/Database-Level-Roles.md).  
  
  
-   **Create an ODBC data source for the instance on your data science client**  
  
     If you create an R solution on a data science client computer and need to connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer as the compute context, you can use either a SQL login, or integrated Windows authentication.  
  
     If you use a SQL login, ensure that the login has appropriate permissions on the database where you will be reading data \(Connect and SELECT permissions, or add the login to the db\_datareader role\). If you need to create objects, you will need DDL admin rights.  To save data to tables, the login to the db\_datawriter role.  
  
     If you use Windows authentication, you must configure an ODBC data source on the data science client that specifies that instance name and other connection information.  
  
    For more information, see [Using the ODBC Data Source Administrator](http://windows.microsoft.com/windows/using-odbc-data-source-administrator).  
  
## Optimizing the Server for R  
 The default settings for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup are intended to optimize the balance of the server for a variety of services supported by the database engine, which might include  ETL processes, reporting, auditing, and applications that use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data. Therefore, under the default settings you  might find resources for R operations restricted or throttled, particularly in memory\-intensive operations.  
  
 To ensure that R tasks are prioritized and resourced appropriately, we recommend that you use Resource Governor to configure an external resource pool specific for R operation. You might also wish to change the amount of memory allocated to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database engine, or increase the number of accounts running under the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service.  
  
-   Configure a resource pool for managing external resources  
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../Topic/CREATE%20EXTERNAL%20RESOURCE%20POOL%20\(Transact-SQL\).md)  
  
-   Change the amount of memory reserved for the database engine  
  
     [Server Memory Server Configuration Options](../../Topics\TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md)  
  
-   Change the number of R accounts that can be started by [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)]  
  
     [Modify the User Account Pool for SQL Server R Services](../../Topics\TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md)  
  
## Get the R Source Code \(Optional\)  
 [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] includes a distribution of the open source R base packages.  
  
 Optionally, click one of these links to immediately begin downloading the modified GPL\/LGPL source code. This is made available in compliance with the GNU General Public License, but is not required to install or use [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].  
  
-   Compatible with RC2 \([.tar archive](http://go.microsoft.com/fwlink/?LinkId=786770)\)  
  
-   Compatible with RC3 \([.tar archive](http://go.microsoft.com/fwlink/?LinkId=786771)\)  
  
## Troubleshooting  
 Run into trouble? See this list of common issues when installing pre\-release versions of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]  
  
 [Upgrade and Installation FAQ &#40;SQL Server R Services&#41;](../Topic/Upgrade%20and%20Installation%20FAQ%20\(SQL%20Server%20R%20Services\).md)  
  
## See Also  
 [Set Up  a Data Science Client](../../Topics\TopicNameContainA/Set-Up--a-Data-Science-Client.md)   
 [Create a Standalone R Server](../../Topics\TopicNameContainA/Create-a-Standalone-R-Server.md)  
  
  