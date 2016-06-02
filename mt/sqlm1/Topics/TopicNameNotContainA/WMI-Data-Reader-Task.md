---
title: WMI Data Reader Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
---
# WMI Data Reader Task
  The WMI Data Reader task runs queries using the Windows Management Instrumentation \(WMI\) Query Language that returns information from WMI about a computer system. You can use the WMI Data Reader task for the following purposes:  
  
-   Query the Windows event logs on a local or remote computer and write the information to a file or variable.  
  
-   Obtain information about the presence, state, or properties of hardware components, and then use this information to determine whether other tasks in the control flow should run.  
  
-   Get a list of applications and determine what version of each application is installed.  
  
 You can configure the WMI Data Reader task in the following ways:  
  
-   Specify the WMI connection manager to use.  
  
-   Specify the source of the WQL query. The query can be stored in a task property, or the query can be stored outside the task, in a variable or a file.  
  
-   Define the format of the WQL query results. The task supports a table, property name\/value pair, or property value format.  
  
-   Specify the destination of the query. The destination can be a variable or a file.  
  
-   Indicate whether the query destination is overwritten, kept, or appended.  
  
 If the source or destination is a file, the WMI Data Reader task uses a File connection manager to connect to the file. For more information, see [Flat File Connection Manager](../../Topics\TopicNameNotContainA/Flat-File-Connection-Manager.md).  
  
 The WMI Data Reader task uses a WMI connection manager to connect to the server from which it reads WMI information. For more information, see [WMI Connection Manager](../../Topics\TopicNameNotContainA/WMI-Connection-Manager.md).  
  
## WQL Query  
 WQL is a dialect of SQL with extensions to support WMI event notification and other WMI\-specific features. For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](http://go.microsoft.com/fwlink/?linkid=7022).  
  
> [!NOTE]  
>  WMI classes vary between versions of Windows.  
  
 The following WQL query returns entries in the Application log event.  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 The following WQL query returns logical disk information.  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 The following WQL query returns a list of the quick fix engineering \(QFE\) updates to the operating system.  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## Custom Logging Messages Available on the WMI Data Reader Task  
 The following table lists the custom log entries for the WMI Data Reader task. For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md) and [Custom Messages for Logging](../../Topics\TopicNameNotContainA/Custom-Messages-for-Logging.md).  
  
|Log entry|Description|  
|---------------|-----------------|  
|**WMIDataReaderGettingWMIData**|Indicates that the task began to read WMI data.|  
|**WMIDataReaderOperation**|Reports the WQL query that the task ran.|  
  
## Configuration of the WMI Data Reader Task  
 You can set properties programmatically or through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [WMI Data Reader Task Editor &#40;WMI Options Page&#41;](../Topic/WMI%20Data%20Reader%20Task%20Editor%20\(WMI%20Options%20Page\).md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For information about programmatically setting these properties, click the following topic:  
  
-   [WmiDataReaderTask](assetId:///T:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask)  
  
## Related Tasks  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  