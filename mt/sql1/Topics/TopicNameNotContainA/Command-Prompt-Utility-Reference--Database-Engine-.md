---
title: "Command Prompt Utility Reference (Database Engine)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
caps.latest.revision: 90
caps.handback.revision: 0
manager: jhubbard
---
# Command Prompt Utility Reference (Database Engine)
Command prompt utilities enable you to script [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] operations. The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
|**Utility**|**Description**|**Installed in**|  
|-----------------|---------------------|----------------------|  
|[bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)|Used to copy data between an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and a data file in a user-specified format.|<*drive*:>\Program Files\\[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta Utility](../../Topics/TopicNameNotContainA/dta-Utility.md)|Used to analyze a workload and recommend physical design structures to optimize server performance for that workload.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[dtexec Utility](../../Topics/TopicNameNotContainA/dtexec-Utility.md)|Used to configure and execute an [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package. A user interface version of this command prompt utility is called **DTExecUI**, which brings up the Execute Package Utility.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]DTS\Binn|  
|[dtutil Utility](../../Topics/TopicNameNotContainA/dtutil-Utility.md)|Used to manage SSIS packages.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]DTS\Binn|  
|[Deploy Model Solutions with the Deployment Utility](../../Topics/TopicNameNotContainA/Deploy-Model-Solutions-with-the-Deployment-Utility.md)|Used to deploy [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] projects to instances of [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)].|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn\VShell\Common7\IDE|  
|[osql Utility](../../Topics/TopicNameNotContainA/osql-Utility.md)|Allows you to enter [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements, system procedures, and script files at the command prompt.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[Profiler Utility](../../Topics/TopicNameNotContainA/Profiler-Utility.md)|Used to start [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] from a command prompt.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[RS.exe Utility (SSRS)](../../Topics/TopicNameNotContainA/RS.exe-Utility--SSRS-.md)|Used to run scripts designed for managing [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] report servers.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[rsconfig Utility (SSRS)](../../Topics/TopicNameNotContainA/rsconfig-Utility--SSRS-.md)|Used to configure a report server connection.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[rskeymgmt Utility (SSRS)](../../Topics/TopicNameNotContainA/rskeymgmt-Utility--SSRS-.md)|Used to manage encryption keys on a report server.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[sqlagent90 Application](../../Topics/TopicNameNotContainA/sqlagent90-Application.md)|Used to start [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent from a command prompt.|<drive\>:\Program Files\Microsoft SQL Server\\<*instance_name*>\MSSQL\Binn|  
|[sqlcmd Utility](../../Topics/TopicNameNotContainA/sqlcmd-Utility.md)|Allows you to enter [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements, system procedures, and script files at the command prompt.|<*drive*:>\Program Files\\[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[SQLdiag Utility](../../Topics/TopicNameNotContainA/SQLdiag-Utility.md)|Used to collect diagnostic information for [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Customer Service and Support.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[sqllogship Application](../../Topics/TopicNameNotContainA/sqllogship-Application.md)|Used by applications to perform backup, copy, and restore operations and associated clean-up tasks for a log shipping configuration without running the backup, copy, and restore jobs.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[SqlLocalDB Utility](../../Topics/TopicNameNotContainA/SqlLocalDB-Utility.md)|An execution mode of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] targeted to program developers.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn\|  
|[sqlmaint Utility](../../Topics/TopicNameNotContainA/sqlmaint-Utility.md)|Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|<drive\>:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[sqlps Utility](../../Topics/TopicNameNotContainA/sqlps-Utility.md)|Used to run PowerShell commands and scripts. Loads and registers the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] PowerShell provider and cmdlets.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn|  
|[sqlservr Application](../../Topics/TopicNameNotContainA/sqlservr-Application.md)|Used to start and stop an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] from the command prompt for troubleshooting.|<drive\>:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Ssms Utility](../../Topics/TopicNameNotContainA/Ssms-Utility.md)|Used to start [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] from a command prompt.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[tablediff Utility](../../Topics/TopicNameNotContainA/tablediff-Utility.md)|Used to compare the data in two tables for non-convergence, which is useful when troubleshooting a replication topology.|[!INCLUDE[ssInstallPathVar](../../Topics/TopicNameContainA/tokens/ssInstallPathVar_md.md)]COM|  
  
 **To access [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager Using [!INCLUDE[win8](../../Topics/TopicNameContainA/tokens/win8_md.md)]**  
  
 Because [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager not does not appear as an application when running [!INCLUDE[win8](../../Topics/TopicNameContainA/tokens/win8_md.md)]. To open [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager12.msc** (for [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]) or **SQLServerManager11.msc** for ([!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]), and then press **Enter**.  
  
## Command Prompt Utilities Syntax Conventions  
  
|**Convention**|**Used for**|  
|--------------------|------------------|  
|UPPERCASE|Statements and terms used at the operating system level.|  
|`monospace`|Sample commands and program code.|  
|*italic*|User-supplied parameters.|  
|**bold**|Commands, parameters, and other syntax that must be typed exactly as shown.|  
  
## See Also  
 [Replication Distribution Agent](../../Topics/TopicNameNotContainA/Replication-Distribution-Agent.md)   
 [Replication Log Reader Agent](../../Topics/TopicNameNotContainA/Replication-Log-Reader-Agent.md)   
 [Replication Merge Agent](../../Topics/TopicNameNotContainA/Replication-Merge-Agent.md)   
 [Replication Queue Reader Agent](../../Topics/TopicNameNotContainA/Replication-Queue-Reader-Agent.md)   
 [Replication Snapshot Agent](../../Topics/TopicNameNotContainA/Replication-Snapshot-Agent.md)