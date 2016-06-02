---
title: SQL Server Agent Jobs for Packages
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
---
# SQL Server Agent Jobs for Packages
  You can automate and schedule the execution of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent. You can schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server, and are stored in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store, and the file system.  
  
## Sections in This Topic  
 This topic contains the following sections:  
  
-   [Scheduling jobs in SQL Server Agent](#jobs)  
  
-   [Scheduling Integration Services packages](#packages)  
  
-   [Troubleshooting scheduled packages](#trouble)  
  
##  <a name="jobs"></a> Scheduling Jobs in SQL Server Agent  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is the service installed by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that lets you automate and schedule tasks by running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent jobs. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service must be running before jobs can run automatically. For more information, see [Configure SQL Server Agent](../Topic/Configure%20SQL%20Server%20Agent.md).  
  
 The **SQL Server Agent** node appears in Object Explorer in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] when you connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
 To automate a recurring task, you create a job by using the **New Job** dialog box. For more information, see [Implement Jobs](../Topic/Implement%20Jobs.md).  
  
 After you create the job, you must add at least one step. A job can include multiple steps, and each step can perform a different task. For more information, see [Manage Job Steps](../Topic/Manage%20Job%20Steps.md).  
  
 After you create the job and the job steps, you can create a schedule for running the job. However you can also create an unscheduled job that you run manually. For more information, see [Create and Attach Schedules to Jobs](../Topic/Create%20and%20Attach%20Schedules%20to%20Jobs.md).  
  
 You can enhance the job by setting notification options, such as specifying an operator to send an e\-mail message to when the job finishes, or adding alerts. For more information, see [Alerts](../Topic/Alerts.md).  
  
##  <a name="packages"></a> Scheduling Integration Services Packages  
 When you create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job to schedule [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages, you must add at least one step and set the type of the step to **SQL Server Integration Services Package**. A job can include multiple steps, and each step can run a different package.  
  
 Running an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package from a job step is like running a package by using the **dtexec** \(dtexec.exe\) and **DTExecUI** \(dtexecui.exe\) utilities. Instead of setting the run\-time options for a package by using command\-line options or the **Execute Package Utility** dialog box, you set the run\-time options in the **New Job Step** dialog box. For more information about the options for running a package, see [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md).  
  
 For more information, see [Schedule a Package by using SQL Server Agent](../../Topics\TopicNameContainA/Schedule-a-Package-by-using-SQL-Server-Agent.md).  
  
 For a video that demonstrates how to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent to run a package, see the video home page, [How to: Automate Package Execution by Using the SQL Server Agent \(SQL Server Video\)](http://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library.  
  
##  <a name="trouble"></a> Troubleshooting  
 A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job step may fail to start a package even though the package runs successfully in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] and from the command line. There are some common reasons for this issue and several recommended solutions. For more information, see the following resources.  
  
-   [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](http://support.microsoft.com/kb/918760)  
  
-   Video, [Troubleshooting: Package Execution Using SQL Server Agent \(SQL Server Video\)](http://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library.  
  
 After a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job step starts a package, the package execution may fail or the package may run successfully but with unexpected results. You can use the following tools to troubleshoot these issues.  
  
-   For packages that are stored in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] MSDB database, the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store, or in a folder on your local machine, you can use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.  
  
     **To use the Log File Viewer, do the following.**  
  
    1.  Right\-click the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job in Object Explorer and then click **View History**.  
  
    2.  Locate the job execution in the **Log file summary** box with the **job failed** message in the **Message** column.  
  
    3.  Expand the job node, and click the job step to view the details of the message in the area below the **Log file summary** box.  
  
-   For packages that are stored in the SSISDB database, you can also use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package. In addition, you can use the reports for the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server.  
  
     **To find information in the reports for the package execution associated with a job execution, do the following.**  
  
    1.  Follow the steps above to view the details of the message for the job step.  
  
    2.  Locate the Execution ID listed in the message.  
  
    3.  Expand the Integration Services Catalog node in Object Explorer.  
  
    4.  Right\-click SSISDB, point to Reports, then Standard Reports, and then click All Executions.  
  
    5.  In the **All Executions** report, locate the Execution ID in the **ID** column. Click **Overview**, **All Messages**, or **Execution Performance** to view information about this package execution.  
  
         For more information about the Overview, All Messages, and Execution Performance reports, see [Reports for the Integration Services Server](../../Topics\TopicNameNotContainA/Reports-for-the-Integration-Services-Server.md).  
  
## External Resources  
  
-   Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](http://support.microsoft.com/kb/918760), on the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Web site  
  
-   Video, [Troubleshooting: Package Execution Using SQL Server Agent \(SQL Server Video\)](http://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library  
  
-   Video, [How to: Automate Package Execution by Using the SQL Server Agent \(SQL Server Video\)](http://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library  
  
-   Technical article, [Checking SQL Server Agent jobs using Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=165675), on mssqltips.com  
  
-   Technical article, [Auto alert for SQL Agent jobs when they are enabled or disabled](http://go.microsoft.com/fwlink/?LinkId=165676), on mssqltips.com  
  
-   Blog entry, [Configuring SQL Agent Jobs to Write to Windows Event Log](http://go.microsoft.com/fwlink/?LinkId=220745), on mssqltips.com.  
  
  