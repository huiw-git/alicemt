---
title: Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
---
# Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service
  This topic describes how to start, stop, pause, resume, or restart the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, or the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager,  [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], **net** commands from a command prompt, [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell.  
  
-   **Before you begin:**  
  
    -   [What are these services?](#Services)  
  
    -   [Additional Information](#MoreInformation)  
  
    -   [Security](#Security)  
  
-   **Instructions using:**  
  
    -   [SQL Server Configuration Manager](#SSCMProcedure)  
  
    -   [SQL Server Management Studio](#SSMSProcedure)  
  
    -   [net Commands from a Command Prompt window](#CommandPrompt)  
  
    -   [Transact\-SQL](#TsqlProcedure)  
  
    -   [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Services"></a> What is the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] service, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service, and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service?  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components are executable programs that run as a Windows service. Programs that run as a Windows service can continue to operate without displaying any activity on the computer screen.  
  
 **[!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] service**  
 The executable process that is the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] can be the default instance \(limit one per computer\), or can be one of many named instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to determine which instances of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] are installed on the computer. The default instance \(if you install it\) is listed as **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(MSSQLSERVER\)**. Named instances \(if you install them\) are listed as **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(\<instance\_name\>\)**. By default, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Express is installed as **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(SQLEXPRESS\)**.  
  
 **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service**  
 A Windows service that executes scheduled administrative tasks, which are called jobs and alerts. For more information, see [SQL Server Agent](../Topic/SQL%20Server%20Agent.md). [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is not available in every edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service**  
 A Windows service that listens for incoming requests for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resources and provides clients information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instances installed on the computer. A single instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service is used for all instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installed on the computer.  
  
###  <a name="MoreInformation"></a> Additional Information  
  
-   Pausing the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] service prevents new users from connecting to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], but users who are already connected can continue to work until their connections are broken. Use pause when you want to wait for users to complete work before you stop the service. This enables them to complete transactions that are in progress. Resume allows the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to accept new connections again. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service cannot be paused or resumed.  
  
-   The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager and [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] display the current status of services by using the following icons.  
  
     **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager**  
  
    -   A green arrow on the icon next to the service name indicates that the service is started.  
  
    -   A red square on the icon next to the service name indicates that the service is stopped.  
  
    -   Two vertical blue lines on the icon next to the service name indicates that the service is paused.  
  
    -   When restarting the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], a red square will indicate that the service stopped, and then a green arrow will indicate that he service started successfully.  
  
     **[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]**  
  
    -   A white arrow on a green circle icon next to the service name indicates that the service is started.  
  
    -   A white square on a red circle icon next to the service name indicates that the service is stopped.  
  
    -   Two vertical white lines on a blue circle icon next to the service name indicates that the service is paused.  
  
-   When using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager or [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], only options that are possible will be available. For example, if the service is already started, **Start** will be unavailable.  
  
-   When running on a cluster, the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] service is best managed by using Cluster Administrator.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 By default, only members of the local administrators group can start, stop, pause, resume or restart a service. To grant non\-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](http://support.microsoft.com/kb/325349). \(The process is similar on other versions of Windows.\)  
  
 Stopping the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] by using the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]**SHUTDOWN** command requires membership in the **sysadmin** or **serveradmin** fixed server roles, and is not transferable.  
  
##  <a name="SSCMProcedure"></a> Using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager  
  
#### Starting [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager  
  
1.  On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
     Because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a snap\-in for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console program and not a stand\-alone program, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager does not appear as an application in newer versions of Windows. Here are the paths to the last four versions when Windows in installed on the C drive.  
  
    |||  
    |-|-|  
    |[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] 2016|C:\\Windows\\SysWOW64\\SQLServerManager13.msc|  
    |[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]|C:\\Windows\\SysWOW64\\SQLServerManager12.msc|  
    |[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]|C:\\Windows\\SysWOW64\\SQLServerManager11.msc|  
    |[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|C:\\Windows\\SysWOW64\\SQLServerManager10.msc|  
  
#### To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]  
  
1.  Start [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, using the instructions above.  
  
2.  If the **User Account Control** dialog box appears, click **Yes**.  
  
3.  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.  
  
4.  In the results pane, right\-click **SQL Server \(MSSQLServer\)** or a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.  
  
5.  Click **OK** to close [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
> [!NOTE]  
>  To start an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] with startup options, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../Topic/Configure%20Server%20Startup%20Options%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
#### To start, stop, pause, resume, or restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser or an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent  
  
1.  Start [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, using the instructions above.  
  
2.  If the **User Account Control** dialog box appears, click **Yes**.  
  
3.  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.  
  
4.  In the results pane, right\-click **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser**, or **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent \(MSSQLServer\)** or **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent \(\<instance\_name\>\)** for a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.  
  
5.  Click **OK** to close [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent cannot be paused.  
  
##  <a name="SSMSProcedure"></a> Using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Studio  
  
#### To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]  
  
1.  In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], right\-click the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] you want to start, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.  
  
     Or, in Registered Servers, right\-click the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] you want to start, point to **Service Control**, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.  
  
2.  If the **User Account Control** dialog box appears, click **Yes**.  
  
3.  When prompted if you want to perform the action, click **Yes**.  
  
#### To start, stop, or restart the an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent  
  
1.  In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], right\-click **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent**, and then click **Start**, **Stop**, or **Restart**.  
  
2.  If the **User Account Control** dialog box appears, click **Yes**.  
  
3.  When prompted if you want to perform the action, click **Yes**.  
  
##  <a name="CommandPrompt"></a> From the Command Prompt Window using net Commands  
 The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services can be started, stopped, or paused by using [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows **net** commands.  
  
###  <a name="dbDefault"></a> To start the default instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]  
  
-   From a command prompt, enter one of the following commands:  
  
     **net start "SQL Server \(MSSQLSERVER\)"**  
  
     \-or\-  
  
     **net start MSSQLSERVER**  
  
###  <a name="dbNamed"></a> To start a named instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]  
  
-   From a command prompt, enter one of the following commands. Replace *\<instancename\>* with the name of the instance you want to manage.  
  
     **net start "SQL Server \(** *instancename* **\)"**  
  
     \-or\-  
  
     **net start MSSQL$** *instancename*  
  
###  <a name="dbStartup"></a> To start the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] with startup options  
  
-   Add startup options to the end of the **net start "SQL Server \(MSSQLSERVER\)"** statement, separated by a space. When started using **net start**, startup options use a slash \(\/\) instead of a hyphen \(\-\).  
  
     **net start "SQL Server \(MSSQLSERVER\)" \/f \/m**  
  
     \-or\-  
  
     **net start MSSQLSERVER \/f \/m**  
  
    > [!NOTE]  
    >  For more information about startup options, see [Database Engine Service Startup Options](../../Topics\TopicNameNotContainA/Database-Engine-Service-Startup-Options.md).  
  
###  <a name="agDefault"></a> To start the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent on the default instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
  
-   From a command prompt, enter one of the following commands:  
  
     **net start "SQL Server Agent \(MSSQLSERVER\)"**  
  
     \-or\-  
  
     **net start SQLSERVERAGENT**  
  
###  <a name="agNamed"></a> To start the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent on a named instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
  
-   From a command prompt, enter one of the following commands. Replace *instancename* with the name of the instance you want to manage.  
  
     **net start "SQL Server Agent\(** *instancename* **\)"**  
  
     \-or\-  
  
     **net start SQLAgent$** *instancename*  
  
 For information about how to run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent in verbose mode for troubleshooting, see [sqlagent90 Application](../../Topics\TopicNameNotContainA/sqlagent90-Application.md).  
  
###  <a name="Browser"></a> To start the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser  
  
-   From a command prompt, enter one of the following commands:  
  
     **net start "SQL Server Browser"**  
  
     \-or\-  
  
     **net start SQLBrowser**  
  
###  <a name="pauseStop"></a> To pause or stop services from the Command Prompt window  
  
-   To pause or stop services modify the commands in the following ways.  
  
    -   To pause a service, replace **net start** with **net pause**.  
  
    -   To stop a service, replace **net start** with use **net stop**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] can be stopped by using the **SHUTDOWN** statement.  
  
#### To stop the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]  
  
-   To wait for currently running [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements and stored procedures to finish, and then stop the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], execute the following statement.  
  
    ```tsql  
    SHUTDOWN;   
    ```  
  
-   To stop the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] immediately, execute the following statement.  
  
    ```tsql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 For more information about the **SHUTDOWN** statement, see [SHUTDOWN &#40;Transact-SQL&#41;](../Topic/SHUTDOWN%20\(Transact-SQL\).md).  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
  
#### To start and stop [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] services  
  
1.  In a Command Prompt window, start [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell by executing the following command.  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  At a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell command prompt, by executing the following command. Replace `computername` with the name of your computer.  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (get-item .).ManagedComputer  
  
    ```  
  
3.  Identify the service that you want to stop or start. Pick one of the following lines. Replace `instancename` with the name of the named instance.  
  
    -   To get a reference to the default instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   To get a reference to a named instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   To get a reference to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service on the default instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   To get a reference to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service on a named instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   To get a reference to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service.  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  Complete the example to start and then stop the selected service.  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## See Also  
 [Overview of SQL Server Setup Documentation](../../Topics\TopicNameNotContainA/Overview-of-SQL-Server-Setup-Documentation.md)   
 [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md)   
 [SQL Server Configuration Manager](../../Topics\TopicNameNotContainA/SQL-Server-Configuration-Manager.md)   
 [Start SQL Server with Minimal Configuration](../../Topics\TopicNameNotContainA/Start-SQL-Server-with-Minimal-Configuration.md)   
 [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)  
  
  