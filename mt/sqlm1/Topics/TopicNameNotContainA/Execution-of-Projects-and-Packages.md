---
title: Execution of Projects and Packages
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
---
# Execution of Projects and Packages
  To run an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package, you can use one of several tools depending on where those packages are stored. The tools are listed in the table below.  
  
 To store a package on the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server, you use the project deployment model to deploy the project to the server. For information, see [Deploy Projects to Integration Services Server](../../Topics\TopicNameNotContainA/Deploy-Projects-to-Integration-Services-Server.md).  
  
 To store a package in the SSIS Package store, the msdb database, or in the file system, you use the package deployment model. For more information, see [Legacy Package Deployment &#40;SSIS&#41;](../Topic/Legacy%20Package%20Deployment%20\(SSIS\).md).  
  
|Tool|Packages that are stored on the Integration Services server|Packages that are stored in the SSIS Package Store or in the msdb database|Packages that are stored in the file system, outside of the location that is part of the SSIS Package Store|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|No|No<br /><br /> However, you can add an existing package to a project from the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store, which includes the msdb database. Adding an existing package to the project in this manner makes a local copy of the package in the file system.|Yes|  
|**SQL Server Management Studio, when you are connected to an instance of the Database Engine that hosts the Integration Services server**<br /><br /> For more information, see [Execute Package Dialog Box](../../Topics\TopicNameNotContainA/Execute-Package-Dialog-Box.md)|Yes|No<br /><br /> However, you can import a package to the server from these locations.|No<br /><br /> However, you can import a package to the server from the file system.|  
|**SQL Server Management Studio, when it is connected to the Integration Services service that manages the SSIS Package Store**|No|Yes|No<br /><br /> However, you can import a package to the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store from the file system.|  
|**dtexec**<br /><br /> For more information, see [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md).|Yes|Yes|Yes|  
|**dtexecui**<br /><br /> For more information, see [Execute Package Utility &#40;DtExecUI&#41; UI Reference](../Topic/Execute%20Package%20Utility%20\(DtExecUI\)%20UI%20Reference.md)|No|Yes|Yes|  
|**SQL Server Agent**<br /><br /> You use a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job To schedule a package.<br /><br /> For more information, see [SQL Server Agent Jobs for Packages](../../Topics\TopicNameNotContainA/SQL-Server-Agent-Jobs-for-Packages.md).|Yes|Yes|Yes|  
|**Built\-in stored procedure**<br /><br /> For more information, see [catalog.start_execution &#40;SSISDB Database&#41;](../Topic/catalog.start_execution%20\(SSISDB%20Database\).md)|Yes|No|No|  
|**Managed API, by using types and members in the** [Microsoft.SqlServer.Management.IntegrationServices](assetId:///N:Microsoft.SqlServer.Management.IntegrationServices) namespace|Yes|No|No|  
|**Managed API, by using types and members in the** [Microsoft.SqlServer.Dts.Runtime](assetId:///N:Microsoft.SqlServer.Dts.Runtime) namespace|Not currently|Yes|Yes|  
  
## Execution and Logging  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages can be enabled for logging and you can capture run\-time information in log files. For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md).  
  
 You can monitor [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages that are deployed to and run on the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server by using operation reports. The reports are available in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For more information, see [Reports for the Integration Services Server](../../Topics\TopicNameNotContainA/Reports-for-the-Integration-Services-Server.md).  
  
## Related Tasks  
  
-   [Schedule a Package by using SQL Server Agent](../../Topics\TopicNameContainA/Schedule-a-Package-by-using-SQL-Server-Agent.md)  
  
-   [Run a Package in SQL Server Data Tools](../../Topics\TopicNameContainA/Run-a-Package-in-SQL-Server-Data-Tools.md)  
  
-   [Run a Package on the SSIS Server Using SQL Server Management Studio](../../Topics\TopicNameContainA/Run-a-Package-on-the-SSIS-Server-Using-SQL-Server-Management-Studio.md)  
  
## See Also  
 [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md)   
 [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md)  
  
  