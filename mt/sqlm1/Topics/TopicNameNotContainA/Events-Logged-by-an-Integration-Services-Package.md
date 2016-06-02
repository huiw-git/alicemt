---
title: Events Logged by an Integration Services Package
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55a0951a-46f3-4f0f-9972-74cec9cc26b7
---
# Events Logged by an Integration Services Package
  An [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package logs various event messages to the Windows Application event log. A package logs these messages when the package starts, when the package stops, and when certain problems occur.  
  
 This topic provides information about the common event messages that a package logs to the Application event log. By default, a package logs some of these messages even if you have not enabled logging on the package. However, there are other messages that the package will log only if you have enabled logging on the package. Regardless of whether the package logs these messages by default or because logging has been enabled, the Event Source for the messages is SQLISPackage.  
  
 For general information about how to run [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages, see [Execution of Projects and Packages](../../Topics\TopicNameNotContainA/Execution-of-Projects-and-Packages.md).  
  
 For information about how to troubleshoot running packages, see [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md).  
  
## Messages about the Status of the Package  
 When you run an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package, the package typically logs various messages about the progress and status of the package. The following table lists those messages.  
  
> [!NOTE]  
>  The package will log the messages in the following table even if you have not enabled logging for the package.  
  
|Event ID|Symbolic Name|Text|Notes|  
|--------------|-------------------|----------|-----------|  
|12288|DTS\_MSG\_PACKAGESTART|Package "" started.|The package has started to run.|  
|12289|DTS\_MSG\_PACKAGESUCCESS|Package "" finished successfully.|The package successfully ran and is no longer running.|  
|12290|DTS\_MSG\_PACKAGECANCEL|Package "%1\!s\!" has been cancelled.|The package is no longer running because the package was canceled.|  
|12291|DTS\_MSG\_PACKAGEFAILURE|Package "" failed.|The package could not run successfully and stopped running.|  
  
 By default, in a new installation, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is configured not to log certain events that are related to the running of packages to the Application event log. This setting prevents too many event log entries when you use the Data Collector feature of the current release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. The events that are not logged are EventID 12288, "Package started," and EventID 12289, "Package finished successfully." To log these events to the Application event log, open the registry for editing. Then in the registry, locate the HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\110\\SSIS node, and change the DWORD value of the LogPackageExecutionToEventLog setting from 0 to 1. However, in an upgrade insallation, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is configured to log these two events. To disable logging, change the value of the LogPackageExecutionToEventLog setting from 1 to 0.  
  
## Messages Associated with Package Logging  
 If you have enabled logging on the package, the Application event log is one of the destinations that is supported by the optional logging features in [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md).  
  
 When you have enabled logging on the package and the log location is the Application event log, the package logs entries that pertain to the following information:  
  
-   Messages about which stage the package is in while the package runs.  
  
-   Messages about particular events that occur while the package runs.  
  
### Messages about the Stages of Package Execution  
  
|Event ID|Symbolic Name|Text|Notes|  
|--------------|-------------------|----------|-----------|  
|12544|DTS\_MSG\_EVENTLOGENTRY|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|When you configure package logging to the Application event log, various messages use this generic format.|  
|12556|DTS\_MSG\_EVENTLOGENTRY\_PACKAGESTART|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|The package started.|  
|12547|DTS\_MSG\_EVENTLOGENTRY\_PREVALIDATE|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|Validation of the object is about to begin.|  
|12548|DTS\_MSG\_EVENTLOGENTRY\_POSTVALIDATE|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|Validation of the object has finished.|  
|12552|DTS\_MSG\_EVENTLOGENTRY\_PROGRESS|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|This generic message reports package progress.|  
|12546|DTS\_MSG\_EVENTLOGENTRY\_POSTEXECUTE|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|The object has finished its work.|  
|12557|DTS\_MSG\_EVENTLOGENTRY\_PACKAGEEND|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|The package has finished running.|  
  
### Messages about Events that Occur  
 The following table lists only some of the messages that are the result of events. For a more comprehensive list of error, warning, and informational messages that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] uses, see [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md).  
  
|Event ID|Symbolic Name|Text|Notes|  
|--------------|-------------------|----------|-----------|  
|12251|DTS\_MSG\_EVENTLOGENTRY\_TASKFAILED|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|The task failed.|  
|12250|DTS\_MSG\_EVENTLOGENTRY\_ERROR|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|This message reports an error that has occurred.|  
|12249|DTS\_MSG\_EVENTLOGENTRY\_WARNING|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|This message reports a warning that has occurred.|  
|12258|DTS\_MSG\_EVENTLOGENTRY\_INFORMATION|Event Name: %1%r Message: %9%r Operator: %2%r Source Name: %3%r Source ID: %4%r Execution ID: %5%r Start Time: %6%r End Time: %7%r Data Code: %8|This message reports informational that is not associated with an error or a warning.|  
  
## Related Tasks  
 For information about how to view log entries in real time, see [View Log Entries in the Log Events Window](../../Topics\TopicNameNotContainA/View-Log-Entries-in-the-Log-Events-Window.md).  
  
## See Also  
 [Events Logged by the Integration Services Service](../../Topics\TopicNameNotContainA/Events-Logged-by-the-Integration-Services-Service.md)  
  
  