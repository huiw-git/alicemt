---
title: SQL Server PowerShell
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
---
# SQL Server PowerShell
  [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] supports Windows PowerShell, which is a powerful scripting shell that lets administrators and developers automate server administration and application deployment. The Windows PowerShell language supports more complex logic than [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts, giving [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] administrators the ability to build robust administration scripts. Windows PowerShell scripts can also be used to administer other [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] server products. This gives administrators a common scripting language across servers.  
  
## SQL Server PowerShell Components  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a Windows PowerShell module named **sqlps** that is used to import the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components into a Windows PowerShell environment or script. The **sqlps** module loads two Windows PowerShell snap\-ins that implement:  
  
-   A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider, which enables a simple navigation mechanism similar to file system paths. You can build paths similar to file system paths, where the drive is associated with a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] management object model, and the nodes are based on the object model classes. You can then use familiar commands such as **cd** and **dir** to navigate the paths similar to the way you navigate folders in a command prompt window. You can use other commands, such as **ren** or **del**, to perform actions on the nodes in the path.  
  
-   A set of cmdlets, which are commands used in Windows PowerShell scripts to specify a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] action. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cmdlets support actions such as running a **sqlcmd** script containing [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] or XQuery statements.  
  
 To learn about Windows PowerShell, see the [Windows PowerShell Getting Started Guide](http://go.microsoft.com/fwlink/?LinkId=217083).  
  
## SQL Server Versions  
 The [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] PowerShell components can be used to manage instances of [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] or later. Instances of [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] must be running SP2 or later. Instances of [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] must be running SP4 or later. When the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] PowerShell components are used with earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], they are limited to the functionality available in those versions.  
  
## SQL Server PowerShell Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes the preferred mechanism for running the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell components; to open a PowerShell session and load the **sqlps** module. The **sqlps** module loads in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell provider and cmdlets, and the SQL Server Management Object \(SMO\) assemblies used by the provider and cmdlets.|[Import the SQLPS Module](../../Topics\TopicNameNotContainA/Import-the-SQLPS-Module.md)|  
|Describes how to load only the SMO assemblies without the provider or cmdlets.|[Load the SMO Assemblies in Windows PowerShell](../../Topics\TopicNameNotContainA/Load-the-SMO-Assemblies-in-Windows-PowerShell.md)|  
|Describes how to run a Windows PowerShell session by right\-clicking a node in **Object Explorer**. [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] launches a Windows PowerShell session, loads the **sqlps** module, and sets the SQL Server provider path to the object selected.|[Run Windows PowerShell from SQL Server Management Studio](../../Topics\TopicNameNotContainA/Run-Windows-PowerShell-from-SQL-Server-Management-Studio.md)|  
|Describes how to create SQL Server Agent job steps that run a Windows PowerShell script. The jobs can then be scheduled to run at specific times or in response to events.|[Run Windows PowerShell Steps in SQL Server Agent](../../Topics\TopicNameNotContainA/Run-Windows-PowerShell-Steps-in-SQL-Server-Agent.md)|  
|Describes how to use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider to navigate a hierarchy of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects.|[SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)|  
|Describes how to use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cmdlets that specify [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] actions such as running a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script.|[Use the Database Engine cmdlets](../../Topics\TopicNameNotContainA/Use-the-Database-Engine-cmdlets.md)|  
|Describes how to specify [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] delimited identifiers that contain characters not supported by Windows PowerShell.|[SQL Server Identifiers in PowerShell](../../Topics\TopicNameNotContainA/SQL-Server-Identifiers-in-PowerShell.md)|  
|Describes how to make SQL Server Authentication connections. By default, the SQL Server PowerShell components use Windows Authentication connections using the Windows credentials of the process running Windows PowerShell.|[Manage Authentication in Database Engine PowerShell](../../Topics\TopicNameNotContainA/Manage-Authentication-in-Database-Engine-PowerShell.md)|  
|Describes how to use variables implemented by the SQL Server PowerShell provider to control how many objects are listed when using Windows PowerShell tab completion. This is particularly useful when working on databases that contain large numbers of objects.|[Manage Tab Completion &#40;SQL Server PowerShell&#41;](../Topic/Manage%20Tab%20Completion%20\(SQL%20Server%20PowerShell\).md)|  
|Describes how to use Get\-Help to get information about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components in the Windows PowerShell environment.|[Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md)|  
  
  