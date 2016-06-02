---
title: Database Engine Scripting
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
---
# Database Engine Scripting
  The [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] supports the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] PowerShell scripting environment to manage instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and the objects in the instances. You can also build and run [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] queries that contain [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] and XQuery in environments very similar to scripting environments.  
  
## SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] includes two [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell snap\-ins that implement:  
  
-   A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell provider that exposes the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] management object model hierarchies as PowerShell paths that are similar to file system paths. You can use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] management object model classes to manage the objects represented at each node of the path.  
  
-   A set of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cmdlets that implement [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] commands. One of the cmdlets is **Invoke\-Sqlcmd**. This is used to run [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query scripts to be run with the **sqlcmd** utility.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides these features for running PowerShell:  
  
-   The **sqlps** PowerShell module that can be imported to a PowerShell session, the module then loads the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] snap\-ins. You can interactively run ad hoc PowerShell commands. You can run script files using a command such as .\\MyFolder\\MyScript.ps1.  
  
-   PowerShell script files can be used as input to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent PowerShell job steps that run the scripts either at scheduled intervals or in response to system events.  
  
-   The **sqlps** utility that starts PowerShell and imports the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] module. You can then perform all actions supported by the module. You can start the **sqlps** utility either in a command prompt or by right\-clicking on the nodes in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Studio Object Explorer tree and selecting **Start PowerShell**.  
  
## Database Engine Queries  
 [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] query scripts contain three types of elements:  
  
-   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] language statements.  
  
-   XQuery language statements  
  
-   Commands and variables from the **sqlcmd** utility.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides three environments for building and running [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] queries:  
  
-   You can interactively run and debug [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] queries in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. You can code and debug several statements in one session, then save all of the statements in a single script file.  
  
-   The **sqlcmd** command prompt utility lets you interactively run [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] queries, and also run existing [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] query script files.  
  
 [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] query script files are typically coded interactively in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] by using the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor. The file can later be opened in one of these environments:  
  
-   Use the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] **File**\/**Open** menu to open the file in a new [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor window.  
  
-   Use the **\-i***input\_file* parameter to run the file with the **sqlcmd** utility.  
  
-   Use the **\-QueryFromFile** parameter to run the file with the **Invoke\-Sqlcmd** cmdlet in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell scripts.  
  
-   Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] job steps to run the scripts either at scheduled intervals or in response to system events.  
  
 In addition, you can use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Generate Script Wizard to generate [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts. You can right\-click objects in the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Object Explorer, then select the **Generate Script** menu item. **Generate Script** launches the wizard, which guides you through the process of creating a script.  
  
## Database Engine Scripting Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to use the code and text editors in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] to interactively develop, debug, and run [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts|[Query and Text Editors &#40;SQL Server Management Studio&#41;](../Topic/Query%20and%20Text%20Editors%20\(SQL%20Server%20Management%20Studio\).md)|  
|Describes how to use the **sqlcmd** utility to run [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts from the command prompt, including the ability to interactively develop scripts.|[sqlcmd How-to Topics](../../Topics\TopicNameNotContainA/sqlcmd-How-to-Topics.md)|  
|Describes how to integrate the SQL Server components into a Windows PowerShell environment and then build PowerShell scripts for managing SQL Server instances and objects.|[SQL Server PowerShell](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell.md)|  
|Describes how to use the **Generate and Publish Scripts** wizard to create [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts that recreate one or more of the objects from a database.|[Generate Scripts &#40;SQL Server Management Studio&#41;](../Topic/Generate%20Scripts%20\(SQL%20Server%20Management%20Studio\).md)|  
  
## See Also  
 [sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md)   
 [Tutorial: Writing Transact-SQL Statements](../Topic/Tutorial:%20Writing%20Transact-SQL%20Statements.md)  
  
  