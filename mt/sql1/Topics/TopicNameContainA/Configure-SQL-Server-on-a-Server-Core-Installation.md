---
title: "Configure SQL Server on a Server Core Installation"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed6e5e94-4b8d-422a-a17e-61b05a4df903
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Configure SQL Server on a Server Core Installation
This topic covers details about configuring [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../Topics/TopicNameContainA/tokens/winserver2008r2_md.md)] SP1. Refer the following sections:  
  
-   [Configure and Manage Server Core on Windows Server](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_ConfigureWindows)  
  
-   [Install SQL Server Updates](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_InstallSQLUpdates)  
  
-   [Start/Stop SQL Server Service](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_StartStopServices)  
  
-   [Enable AlwaysOn Availability Groups](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_EnableAlwaysON)  
  
-   [Configuring Remote Access of SQL Server Running on Server Core](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_ConfigureRemoteAccess)  
  
-   [SQL Server Profiler](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_Profiler)  
  
-   [SQL Server Auditing](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_Auditing)  
  
-   [Command Prompt Utilities](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_CMD)  
  
-   [Use troubleshooting tools](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#BKMK_troubleshoot)  
  
##  <a name="BKMK_ConfigureWindows"></a> Configure and Manage Server Core on Windows Server  
 The section provides references to the topics that help configure and manage a Server Core installation.  
  
 Not all features of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] are supported in Server Core mode.  Some of these features can be installed on a client computer or a different server that is not running Server Core, and connected to the Database Engine services installed on Server Core.  
  
 For more information about configuring and managing a Server Core installation remotely, see the following topics:  
  
-   [Windows Server 2008 R2: Best Practices for Server Core Deployments](http://go.microsoft.com/fwlink/?LinkID=245957) (http://go.microsoft.com/fwlink/?LinkID=245957)  
  
-   [Configuring a Server Core installation: Overview](http://go.microsoft.com/fwlink/?LinkId=245958) (http://go.microsoft.com/fwlink/?LinkId=245958)  
  
-   [Configuring a Server Core installation of Windows Server 2008 R2 with Sconfig.cmd](http://go.microsoft.com/fwlink/?LinkId=245959) (http://go.microsoft.com/fwlink/?LinkId=245959)  
  
-   [Installing a server role on a server running a Server Core installation of Windows Server 2008 R2: Overview](http://go.microsoft.com/fwlink/?LinkId=245960) (http://go.microsoft.com/fwlink/?LinkId=245960)  
  
-   [Installing Windows Features on a server running a Server Core installation of Windows Server 2008 R2: Overview](http://go.microsoft.com/fwlink/?LinkId=245961) (http://go.microsoft.com/fwlink/?LinkId=245961)  
  
-   [Managing a Server Core installation: Overview](http://go.microsoft.com/fwlink/?LinkId=245962) (http://go.microsoft.com/fwlink/?LinkId=245962)  
  
-   [Administering a Server Core installation](http://go.microsoft.com/fwlink/?LinkId=245963) (http://go.microsoft.com/fwlink/?LinkId=245963)  
  
##  <a name="BKMK_InstallSQLUpdates"></a> Install [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Updates  
 This section provides information about installing updates for [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] on a Windows Server Core machine. We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates. For more information about installing [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] on a Windows Server Core machine, see [Install SQL Server 2016 on Server Core](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-on-Server-Core.md).  
  
 The following are the two scenarios for installing product updates:  
  
-   [Installing Updates for SQL Server 2016 during a new installation](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#bkmk_NewInstall)  
  
-   [Installing Updates for SQL Server 2016 after it has already been installed](../../Topics/TopicNameContainA/Configure-SQL-Server-on-a-Server-Core-Installation.md#bkmk_alreadyInstall)  
  
###  <a name="bkmk_NewInstall"></a> Installing Updates for [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] During a New Installation  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup supports only command prompt installations on Server Core operating system. For more information, see [Install SQL Server 2016 from the Command Prompt](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.  
  
 After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup process. Product Update can pull in a cumulative update, service pack, or service pack plus cumulative update.  
  
 Specify the UpdateEnabled, and UpdateSource parameters to include the latest product updates with the main product installation. Refer the following example to enable product updates during the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup:  
  
```tsql  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /UpdateEnabled=True /UpdateSource=”<SourcePath>” /IACCEPTSQLSERVERLICENSETERMS  
```  
  
###  <a name="bkmk_alreadyInstall"></a> Installing Updates for [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] After It Has Been Installed  
 On an installed instance of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], we recommend that you apply the latest security updates and critical updates including General Distribution Releases (GDRs), and Service Packs (SPs). Individual Cumulative updates and security updates should be adopted on a case-by-case, "as-needed" basis. Evaluate the update; if it's needed, then apply it.  
  
 Apply an update at a command prompt, replacing <package_name> with the name of your update package:  
  
-   Update a single instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and all shared components. You can specify the instance either by using the InstanceName parameter or the InstanceID parameter.  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance  
    ```  
  
-   Update [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] shared components only:  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
    ```  
  
-   Update all instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] on the computer and all shared components:  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances  
    ```  
  
##  <a name="BKMK_StartStopServices"></a> Start/Stop [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Service  
 The [sqlservr Application](../../Topics/TopicNameNotContainA/sqlservr-Application.md) application starts, stops, pauses, and continues an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] from a command prompt.  
  
 You can also use Net services to start and stop the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] services.  
  
##  <a name="BKMK_EnableAlwaysON"></a> Enable AlwaysOn Availability Groups  
 Being enabled for AlwaysOn Availability Groups is a prerequisite for a server instance to use availability groups as a high availability and disaster recovery solution. For more information about managing the AlwaysOn Availability Groups, see [Enable and Disable Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Enable-and-Disable-Always-On-Availability-Groups--SQL-Server-.md).  
  
### Using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager Remotely  
 These steps are meant to be performed on a PC running the client edition of [!INCLUDE[win7](../../Topics/TopicNameContainA/tokens/win7_md.md)] or later, or another server that has the Server Graphical Shell installed (i.e. a full installation of [!INCLUDE[winserver2008r2](../../Topics/TopicNameContainA/tokens/winserver2008r2_md.md)] or a [!INCLUDE[win8srv](../../Topics/TopicNameContainA/tokens/win8srv_md.md)] installation with the Server Graphical Shell feature enabled).  
  
1.  Open Computer Management. To open Computer Management do one of the following:  
  
    1.  On [!INCLUDE[win7](../../Topics/TopicNameContainA/tokens/win7_md.md)], Windows Server 2008, or [!INCLUDE[winserver2008r2](../../Topics/TopicNameContainA/tokens/winserver2008r2_md.md)]:  
  
        1.  Click Start, click All Programs, click Administrative Tools, and then click Computer Management.  
  
        2.  Click Start, click Run, type COMPMGMT.MSC, and then click OK.  
  
    2.  On [!INCLUDE[win8srv](../../Topics/TopicNameContainA/tokens/win8srv_md.md)] with Server Graphical Shell enabled:  
  
        1.  Move your mouse to the bottom-left corner of the screen and right-click when you see the Start overlay.  
  
        2.  Select Computer Management  from the context menu.  
  
2.  In the console tree, right-click Computer Management, and then click Connect to another computer.  
  
3.  In the Select Computer dialog box, type the name of the Server Core machine that you want to manage, or click Browse to find it, and then click OK.  
  
4.  In the console tree, under Computer Management of the Server Core machine, click Services and Applications.  
  
5.  Double click [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager.  
  
6.  In [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, click [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Services, right-click [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] (<instance name\>), where <instance name\> is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click Properties.  
  
7.  Select the AlwaysOn High Availability tab.  
  
8.  Verify that Windows failover cluster name field contains the name of the local failover cluster node. If this field is blank, this server instance currently does not support AlwaysOn Availability Groups. Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] that does not support AlwaysOn Availability Groups.  
  
9. Select the Enable AlwaysOn Availability Groups check box, and click OK.  
  
10. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager saves your change. Then, you must manually restart the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service. This enables you to choose a restart time that is best for your business requirements. When the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service restarts, AlwaysOn will be enabled, and the IsHadrEnabled server property will be set to 1.  
  
> [!NOTE]  
>  -   You must have the appropriate user rights or you must have been delegated the appropriate authority on the target computer to connect to that computer.  
> -   The name of the computer that you are managing appears in parentheses next to Computer Management in the console tree.  
  
### Using PowerShell Cmdlets to Enable AlwaysOn Availability Groups  
 The PowerShell Cmdlet, Enable-SqlAlwaysOn, is used to enable AlwaysOn Availability Group on an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. If AlwaysOn Availability Groups is enable while the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service is running, the Database Engine service must be restarted for the change to complete. Unless you specify the -Force parameter, the cmdlet prompts you to ask whether you wish to restart the service; if cancelled, no operation occurs.  
  
 You must have Administrator permissions to execute this cmdlet.  
  
 You can use one of the following syntaxes to enable AlwaysOn Availability Groups for an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]:  
  
```  
Enable-SqlAlwaysOn [-Path <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn -InputObject <Server> [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn [-ServerInstance <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
 The following PowerShell command enables AlwaysOn Availability Groups on an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] (Machine\Instance):  
  
```  
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Machine\Instance  
```  
  
##  <a name="BKMK_ConfigureRemoteAccess"></a> Configuring Remote Access of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Running on Server Core  
 Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] instance that is running on [!INCLUDE[winserver2008r2](../../Topics/TopicNameContainA/tokens/winserver2008r2_md.md)] Server Core SP1.  
  
### Enable remote connections on the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]  
 To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### Enable and start the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser service  
 By default, the Browser service is disabled.  If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] running on Server Core, run the following command from the command prompt to enable it:  
  
 `sc config SQLBROWSER start= auto`  
  
 After it is enabled, run the following command from the command prompt to start the service:  
  
 `net start SQLBROWSER`  
  
### Create exceptions in Windows Firewall  
 To create exceptions for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../Topics/TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md).  
  
### Enable TCP/IP on the Instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]  
 The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] on Server Core. Follow these steps:  
  
1.  On the computer that is running Windows Server 2008 R2 Server Core SP1, launch Task Manager.  
  
2.  On the **Applications** tab, click **New Task**.  
  
3.  In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**. This opens the **Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Powershell** window.  
  
4.  In the **Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:  
  
```  
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
##  <a name="BKMK_Profiler"></a> [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Profiler  
 On a remote machine, start [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] and select New Trace from the File menu, the application displays a Connect to Server dialog box where you can specify the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance, residing on the Server Core machine, to which you want to connect. For more information, see [Start SQL Server Profiler](../../Topics/TopicNameNotContainA/Start-SQL-Server-Profiler.md).  
  
 For more information on the permissions required to run [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)], see [Permissions Required to Run SQL Server Profiler](../../Topics/TopicNameNotContainA/Permissions-Required-to-Run-SQL-Server-Profiler.md).  
  
 For additional details about [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)], see [SQL Server Profiler](../../Topics/TopicNameNotContainA/SQL-Server-Profiler.md).  
  
##  <a name="BKMK_Auditing"></a> [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Auditing  
 You can use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] remotely to define an audit. After the audit is created and enabled, the target will receive entries. For more information about creating and managing [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audits, see [SQL Server Audit (Database Engine)](../../Topics/TopicNameNotContainA/SQL-Server-Audit--Database-Engine-.md).  
  
##  <a name="BKMK_CMD"></a> Command Prompt Utilities  
 You can use the following command prompt utilities that enable you to script [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] operations on a Server Core machine. The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] for Server Core:  
  
|**Utility**|**Description**|**Installed in**|  
|-----------------|---------------------|----------------------|  
|[bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)|Used to copy data between an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and a data file in a user-specified format.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[dtexec Utility](../../Topics/TopicNameNotContainA/dtexec-Utility.md)|Used to configure and execute an [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]DTS\Binn|  
|[dtutil Utility](../../Topics/TopicNameNotContainA/dtutil-Utility.md)|Used to manage SSIS packages.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]DTS\Binn|  
|[osql Utility](../../Topics/TopicNameNotContainA/osql-Utility.md)|Allows you to enter [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements, system procedures, and script files at the command prompt.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[sqlagent90 Application](../../Topics/TopicNameNotContainA/sqlagent90-Application.md)|Used to start [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent from a command prompt.|<drive\>:\Program Files\\[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]\\<*instance_name*>\MSSQL\Binn|  
|[sqlcmd Utility](../../Topics/TopicNameNotContainA/sqlcmd-Utility.md)|Allows you to enter [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements, system procedures, and script files at the command prompt.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[SQLdiag Utility](../../Topics/TopicNameNotContainA/SQLdiag-Utility.md)|Used to collect diagnostic information for [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Customer Service and Support.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[sqlmaint Utility](../../Topics/TopicNameNotContainA/sqlmaint-Utility.md)|Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|<drive\>:\Program Files\\[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[sqlps Utility](../../Topics/TopicNameNotContainA/sqlps-Utility.md)|Used to run PowerShell commands and scripts. Loads and registers the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] PowerShell provider and cmdlets.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[sqlservr Application](../../Topics/TopicNameNotContainA/sqlservr-Application.md)|Used to start and stop an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] from the command prompt for troubleshooting.|<drive\>:\Program Files\\[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
  
##  <a name="BKMK_troubleshoot"></a> Use troubleshooting tools  
 You can use [SQLdiag Utility](../../Topics/TopicNameNotContainA/SQLdiag-Utility.md) to collect logs and data files from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers. SQLdiag is intended to expedite and simplify diagnostic information gathering for Microsoft Customer Support Services.  
  
 You can launch the utility on the administrator command prompt on the Server Core, using the syntax specified in the topic: [SQLdiag Utility](../../Topics/TopicNameNotContainA/SQLdiag-Utility.md).  
  
## See Also  
 [Install SQL Server 2016 on Server Core](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-on-Server-Core.md)   
 [Installation How-to Topics](../../Topics/TopicNameNotContainA/Installation-How-to-Topics.md)