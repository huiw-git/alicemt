---
title: Command Prompt Utility Reference (Database Engine)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
---
# Command Prompt Utility Reference (Database Engine)
  Command prompt utilities enable you to script [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] operations. The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|**Utility**|**Description**|**Installed in**|  
|-----------------|---------------------|----------------------|  
|[bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)|Used to copy data between an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and a data file in a user\-specified format.|\<*drive*:\>\\Program Files\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\Client SDK\\ODBC\\110\\Tools\\Binn|  
|[dta Utility](../../Topics\TopicNameNotContainA/dta-Utility.md)|Used to analyze a workload and recommend physical design structures to optimize server performance for that workload.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md)|Used to configure and execute an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package. A user interface version of this command prompt utility is called **DTExecUI**, which brings up the Execute Package Utility.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]DTS\\Binn|  
|[dtutil Utility](../../Topics\TopicNameNotContainA/dtutil-Utility.md)|Used to manage SSIS packages.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]DTS\\Binn|  
|[Deploy Model Solutions with the Deployment Utility](../../Topics\TopicNameNotContainA/Deploy-Model-Solutions-with-the-Deployment-Utility.md)|Used to deploy [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] projects to instances of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn\\VShell\\Common7\\IDE|  
|[osql Utility](../../Topics\TopicNameNotContainA/osql-Utility.md)|Allows you to enter [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements, system procedures, and script files at the command prompt.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[Profiler Utility](../../Topics\TopicNameNotContainA/Profiler-Utility.md)|Used to start [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] from a command prompt.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[RS.exe Utility &#40;SSRS&#41;](../Topic/RS.exe%20Utility%20\(SSRS\).md)|Used to run scripts designed for managing [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report servers.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[rsconfig Utility &#40;SSRS&#41;](../Topic/rsconfig%20Utility%20\(SSRS\).md)|Used to configure a report server connection.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[rskeymgmt Utility &#40;SSRS&#41;](../Topic/rskeymgmt%20Utility%20\(SSRS\).md)|Used to manage encryption keys on a report server.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[sqlagent90 Application](../../Topics\TopicNameNotContainA/sqlagent90-Application.md)|Used to start [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent from a command prompt.|\<drive\>:\\Program Files\\Microsoft SQL Server\\\<*instance\_name*\>\\MSSQL\\Binn|  
|[sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md)|Allows you to enter [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements, system procedures, and script files at the command prompt.|\<*drive*:\>\\Program Files\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\Client SDK\\ODBC\\110\\Tools\\Binn|  
|[SQLdiag Utility](../../Topics\TopicNameNotContainA/SQLdiag-Utility.md)|Used to collect diagnostic information for [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Customer Service and Support.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[sqllogship Application](../../Topics\TopicNameNotContainA/sqllogship-Application.md)|Used by applications to perform backup, copy, and restore operations and associated clean\-up tasks for a log shipping configuration without running the backup, copy, and restore jobs.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[SqlLocalDB Utility](../../Topics\TopicNameNotContainA/SqlLocalDB-Utility.md)|An execution mode of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] targeted to program developers.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn\\|  
|[sqlmaint Utility](../../Topics\TopicNameNotContainA/sqlmaint-Utility.md)|Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|\<drive\>:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Binn|  
|[sqlps Utility](../../Topics\TopicNameNotContainA/sqlps-Utility.md)|Used to run PowerShell commands and scripts. Loads and registers the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell provider and cmdlets.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn|  
|[sqlservr Application](../../Topics\TopicNameNotContainA/sqlservr-Application.md)|Used to start and stop an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] from the command prompt for troubleshooting.|\<drive\>:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Binn|  
|[Ssms Utility](../../Topics\TopicNameNotContainA/Ssms-Utility.md)|Used to start [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] from a command prompt.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]Tools\\Binn\\VSShell\\Common7\\IDE|  
|[tablediff Utility](../../Topics\TopicNameNotContainA/tablediff-Utility.md)|Used to compare the data in two tables for non\-convergence, which is useful when troubleshooting a replication topology.|[!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]COM|  
  
 **To access [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager Using [!INCLUDE[win8](../../Token\Other/win8_md.md)]**  
  
 Because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a snap\-in for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console program and not a stand\-alone program, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager not does not appear as an application when running [!INCLUDE[win8](../../Token\Other/win8_md.md)]. To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager12.msc** \(for [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]\) or **SQLServerManager11.msc** for \([!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]\), and then press **Enter**.  
  
## Command Prompt Utilities Syntax Conventions  
  
|**Convention**|**Used for**|  
|--------------------|------------------|  
|UPPERCASE|Statements and terms used at the operating system level.|  
|`monospace`|Sample commands and program code.|  
|*italic*|User\-supplied parameters.|  
|**bold**|Commands, parameters, and other syntax that must be typed exactly as shown.|  
  
## See Also  
 [Replication Distribution Agent](../../Topics\TopicNameNotContainA/Replication-Distribution-Agent.md)   
 [Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md)   
 [Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md)   
 [Replication Queue Reader Agent](../../Topics\TopicNameNotContainA/Replication-Queue-Reader-Agent.md)   
 [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md)  
  
  