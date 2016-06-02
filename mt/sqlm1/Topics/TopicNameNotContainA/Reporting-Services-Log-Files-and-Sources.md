---
title: Reporting Services Log Files and Sources
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
---
# Reporting Services Log Files and Sources
  A report server and report server environment uses a variety of log destinations to record information about server operations and status. There are two basic categories of logging, execution logging and trace logging. Execution logging includes information about report execution statistics, auditing, performance diagnosis and optimization. Trace logging is information about error messages and general diagnostics.  
  
 **[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode | [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode  
  
 The following table provides links to additional information about each log, including the log location and how to view the log contents.  
  
|Log|Description|  
|---------|-----------------|  
|[Report Server ExecutionLog and the ExecutionLog3 View](../../Topics\TopicNameNotContainA/Report-Server-ExecutionLog-and-the-ExecutionLog3-View.md)|The execution log is a SQL Server view stored in the report server database.<br /><br /> The report server execution log contains data about specific reports, including when a report was run, who ran it, where it was delivered, and which rendering format was used.|  
|SharePoint trace log|For report servers running in SharePoint, the SharePoint trace logs contains [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] information. You can also configure [!INCLUDE[ssRS](../../Token\Other/ssRS_md.md)] specific information for the SharePoint Unified Logging service. For more information, see [Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](../Topic/Turn%20on%20Reporting%20Services%20events%20for%20the%20SharePoint%20trace%20log%20\(ULS\).md)|  
|[Report Server Service Trace Log](../../Topics\TopicNameNotContainA/Report-Server-Service-Trace-Log.md)|The service trace log contains very detailed information that is useful if you are debugging an application or investigating an issue or event. The trace log files are ReportServerService\_\<timestamp\>.log and are located in the following folder:<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`|  
|[Report Server HTTP Log](../../Topics\TopicNameNotContainA/Report-Server-HTTP-Log.md)|The HTTP log file contains a record of all HTTP requests and responses handled by the Report Server Web service and Report Manager.|  
|[Windows Application Log](../../Topics\TopicNameNotContainA/Windows-Application-Log.md)|The Microsoft Windows Application log contains information about report server events.|  
|Windows Performance logs|The Windows Performance logs contain report server performance data. You can create performance logs, and then choose counters that determine which data to collect. For more information, see [Monitoring Report Server Performance](../../Topics\TopicNameNotContainA/Monitoring-Report-Server-Performance.md).|  
|SQL Server Setup log files|Log files are also created during Setup. If Setup fails or succeeds with warnings or other messages, you can examine the log files to troubleshoot the problem. For more information, see [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md).|  
|IIS Logs|Log files created by Microsoft Internet Information Services \(IIS\). For more information, see [How to enable logging in Internet Information Services \(IIS\)](http://support.microsoft.com/kb/313437) \(http:\/\/support.microsoft.com\/kb\/313437\).|  
  
## See Also  
 [Reporting Services Report Server &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Report%20Server%20\(Native%20Mode\).md)   
 [Errors and Events Reference &#40;Reporting Services&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Reporting%20Services\).md)  
  
  