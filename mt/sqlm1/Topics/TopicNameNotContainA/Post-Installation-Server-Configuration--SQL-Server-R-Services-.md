---
title: Post-Installation Server Configuration (SQL Server R Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b32d43de-7e9c-4ae4-a110-d8d56b514172
robots: noindex,nofollow
---
# Post-Installation Server Configuration (SQL Server R Services)
  After you install the [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)] on [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], and you have installed the necessary R components, you must perform some additional steps to register the R extensions, and to provision required accounts.  
  
> [!WARNING]  
>  Running the configuration script that enables [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] will require a restart of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
>   
>  If you previously installed [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] and want to upgrade, you must uninstall the previous CTP version of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and then reinstall the latest CTP. You must also use the updated script available from the Microsoft Download Center.  
>   
>  For uninstall instructions, see [Upgrade and Installation FAQ &#40;SQL Server R Services&#41;](../Topic/Upgrade%20and%20Installation%20FAQ%20\(SQL%20Server%20R%20Services\).md).  
  
 Note that these instructions apply only to the following pre\-release versions of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] CTP 3.0, 3.1, 3.2, and 3.3  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC0, RC1  
  
## 1. Enable external scripts \(required\)  
 When you installed the [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)] as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup, the extensions are installed, but by default scripts are **not** enabled. Therefore, you must enable the execution of external scripts by running [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md).  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to the instance where you installed the feature.  
  
2.  Open a new **Query** window and run the following command:  
  
    ```  
    exec sp_configure 'external scripts enabled', 1;   
    reconfigure;  
    ```  
  
## 2. Run the post\-installation script \(required\)  
 For pre\-release versions of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], a  script has been provided to help you configure the necessary accounts, register the R runtime, and set up the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service.  
  
 Different versions of the script are provided, depending on which build you install.  
  
-   If you are installing CTP 3.0, use the script that is included with setup.  
  
-   If you are installing CTP versions 3.1, 3.2, or 3.3, you must download an updated version of the [post\-installation configuration script](http://go.microsoft.com/fwlink/?LinkId=723194) from the Microsoft Download Center. The updated version supports de\-registration of older components.  
  
     Click the link and select **Save As** to save the script to a local folder. Rename the existing script, and then copy the new script into the folder where the script will be executed.  
  
     If you are installing RC1, the updated script is included with setup, so you do not need to download it.  
  
1.  On the server where you enabled [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)], locate the file **registerRext.exe**.  
  
     If you installed using defaults, the script file is located in this directory:  
  
     `C:\Program Files\RRO\RRO-3.2.2-for-RRE-7.5.0\R-3.2.2\library\RevoScaleR\rxLibs\x64`  
  
    > [!NOTE]  
    >  If you have obtained an updated version of the script, the script must be copied to the default folder \(or the folder containing the **rx** libraries\)  before you run it. If you run the script in a different folder you might get this error:  
    >   
    >  Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'ArgumentParser' or one of its dependencies. The system cannot find the file specified at Microsoft.SqlServer.Server.Program.Main\(String\[\] args\)  
  
2.  Open a command prompt **with administrative privileges**, and run the following command:  
  
     **Default instance**  
  
    ```  
    registerRext.exe /install  
    ```  
  
    > [!NOTE]  
    >  Note: This example assumes that you installed to the default location. If you performed a custom install, verify the location of the **rx** libraries and edit the path as needed.  
  
     **Named instance**  
  
     If you have installed the [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)] on a named instance, add the *instance:* argument and specify the instance name, as shown in this example:  
  
    ```  
    registerRext.exe  /install /instance:SQLNamedInstance  
    ```  
  
    > [!NOTE]  
    >  You do not need to include the host computer name when specifying a named instance.  
  
     **Using PowerShell**  
  
     To run **registerRext.exe** using PowerShell:  
  
    ```  
    &"${env:programfiles}\RRO\RRO-3.2.2-for-RRE-7.5.0\R-3.2.2\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe" /install /instance:<SQL Server instance name>  
    ```  
  
     This PowerShell command uses the `call (&)` operator to call **registerRext.exe**, using an environment variable, and pass it the name of the instance.  
  
     For more information, see  [Using environment variables with Windows PowerShell](http://blogs.technet.com/b/tip_of_the_day/archive/2014/05/14/tip-of-the-day-using-environment-variables-with-windows-powershell.aspx) and  [The CALL Operator](http://social.technet.microsoft.com/wiki/contents/articles/7703.powershell-running-executables.aspx).  
  
3.  If you have performed all installation steps in order, you do not need to restart the instance; the script will restart the service for you.  
  
 **Notes:**  
  
 Running this script performs the following actions on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance:  
  
-   Stops the SQL services.  
  
-   Copies the file for the R stored procedures and Rlauncher.exe into the SQL bin path.  
  
-   Creates a user pool named SQLRUserGroup, if one does not already exist, and adds users with the names SQLRUser\_1, SQLRUser\_2, etc.  
  
     These accounts are low privilege accounts used for running individual sessions of the R runtime and are separate from any SQL logins that you might create for remote R job execution. By default 20 users are added, but you can change this value. For more information, see [Configure and Manage Advanced Analytics Extensions](../../Topics\TopicNameNotContainA/Configure-and-Manage-Advanced-Analytics-Extensions.md).  
  
-   Registers several extended stored procedures with the database engine.  
  
-   Creates a database role, **db\_rrerole**.  
  
-   Stops and restarts the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service.  
  
-   Restarts the SQL services.  
  
 See the log file created by the script, RegisterRExt.log, for details. The log file is created in the same location as RegisterRExt.exe.  
  
## 3. Increase the amount of memory allocated to R processes \(recommended\)  
 If you plan to use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer to perform tasks beyond simply testing the R scripting feature, and you are using the default settings for the running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance, you might find that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses most of the memory on the computer and does not leave enough memory for R. To mitigate this, you can reduce the maximum amount of machine memory used by the server to 80% of the available physical memory.  
  
 For information about how to modify the amount of physical memory allocated to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Server Memory Server Configuration Options](../../Topics\TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md).  
  
## 4. Set up a database and enable access for ScaleR functions to individual databases  
  
1.  If you do not have any existing databases, you should create one now for use in experimenting with R functions.  
  
     For example, the [product samples](https://www.microsoft.com/en-us/download/details.aspx?id=49502) include several [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts that you can use to create a database, provision users as SQL logins, and create sample tables. Many of these samples use the Iris sample dataset which is familiar to data scientists.  
  
     The sample scripts are included in the Advanced Analytics folder of the .zip file included in the product samples:  
  
    -   **sample\_db\_setup.sql**: Creates a database named sqlr and a user. The sample script is provided only for reference; be sure to customize the user name and password.  
  
    -   **iris\_demo.sql**: Creates a table and populates the table with data from an R package.  
  
         This script also creates and trains several models, so we recommend that you walk through it step by step.  
  
2.  On each database that you want to access using the **RevoScaleR** functions, run the following statement in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to create a SQL login:  
  
    ```  
    USE <target database name>  
      GO  
      CREATE LOGIN [<login name>] WITH PASSWORD= '<password>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;  
      CREATE USER [<user name>] FOR LOGIN [<login name>] WITH DEFAULT_SCHEMA=[db_datareader]  
      ALTER ROLE [db_datareader] ADD MEMBER [<user name>]  
  
    ```  
  
    > [!NOTE]  
    >  Be sure to substitute an actual user login and password of your choosing.  
    >   
    >  Note that SQL authentication is required only if you want to use the RevoScaleR functions to change execution context. For generic R script execution using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], Windows authentication is preferred.  
  
3.  Run the following statement to add the user you just created to the role,  **db\_rrerole**. This role allows the user or login to execute the stored procedures that call R code.  
  
    ```  
    USE [master]  
      GO  
       CREATE USER [<user name>] FOR LOGIN [<login name>] WITH DEFAULT_SCHEMA=[db_rrerole]  
       ALTER ROLE [db_rrerole] ADD MEMBER [<user name>]  
  
    ```  
  
4.  Verify that the login has been created and has the necessary permissions.  
  
    -   At the instance level, expand **Security**, double\-click the login you just created, and click **User Mapping**.  
  
         In **Users mapped to this login**, ensure that the default schema is **db\_datareader**, if the login needs to read SQL data for R jobs. Change the default schema to **db\_datawriter** if the login will need to save results to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or run DDL statements.  
  
    -   In **Database role membership**, ensure that the login has been added to the **db\_rrerole** for the master database.  
  
## Verify Access to R Runtime  
 After installation is complete, start by verifying that the extensions are enabled and that you can run R code using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
#### To verify that you can use R  
  
1.  Open [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] and connect to the instance where you enabled [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)].  
  
2.  Open a new **Query** window and type `sp_configure`. If the extensions are enabled, the value of `'external scripts enabled'` should be 1.  
  
3.  To verify that you can run R code from [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], open a new **Query** window, and use a simple statement like this one:  
  
    ```  
    exec sp_execute_external_script  @language =N'r',  
    @script=N'OutputDataSet<-InputDataSet',    
    @input_data_1 =N'select 1 as hello'  
    with result sets (([hello] int not null));  
    go  
    ```  
  
 After installation is complete, you can use R and SQL together in many ways. For examples, see [SQL Server R Services Tutorials](../Topic/SQL%20Server%20R%20Services%20Tutorials.md).  
  
## Additional Steps to Enable Remote Access  
 Typically a data scientist will work from a separate workstation that has the R development tools, and use the data science client computer for  developing and testing custom R code. However, to access [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data from R, or to use remote compute contexts, you need to enable firewall access for the  **sqlserver.exe** executable.  
  
 For more information about how to do this, see [Configure the Windows Firewall to Allow SQL Server Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md).  
  
## Next Steps  
 Some properties of the service can be changed after installation. For more information, see [Configure and Manage Advanced Analytics Extensions](../../Topics\TopicNameNotContainA/Configure-and-Manage-Advanced-Analytics-Extensions.md).  
  
  