---
title: WMI Data Reader Task Editor (WMI Options Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
---
# WMI Data Reader Task Editor (WMI Options Page)
  Use the **WMI Options** page of the **WMI Data Reader Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language \(WQL\) query and the destination of the query result.  
  
 To learn about this task, see [WMI Data Reader Task](../../Topics\TopicNameNotContainA/WMI-Data-Reader-Task.md). For more information about WMI Query Language \(WQL\), see the Windows Management Instrumentation topic, [Querying with WQL](http://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.  
  
## Static Options  
 **WMIConnectionName**  
 Select a WMI connection manager in the list, or click \<**New WMI Connection…**\> to create a new connection manager.  
  
 **Related Topics:** [WMI Connection Manager](../../Topics\TopicNameNotContainA/WMI-Connection-Manager.md), [WMI Connection Manager Editor](../../Topics\TopicNameNotContainA/WMI-Connection-Manager-Editor.md)  
  
 **WQLQuerySourceType**  
 Select the source type of the WQL query that the task runs. This property has the options listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|**Direct input**|Set the source to a WQL query. Selecting this value displays the dynamic option **WQLQuerySourceType**.|  
|**File connection**|Select a file that contains the WQL query. Selecting this value displays the dynamic option **WQLQuerySourceType**.|  
|**Variable**|Set the source to a variable that defines the WQL query. Selecting this value displays the dynamic option **WQLQuerySourceType**.|  
  
 **OutputType**  
 Specify whether the output should be a data table, property value, or property name and value.  
  
 **OverwriteDestination**  
 Specifies whether to keep, overwrite, or append to the original data in the destination file or variable.  
  
 **DestinationType**  
 Select the destination type of the WQL query that the task runs. This property has the options listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|**File connection**|Select a file to save the results of the WQL query in. Selecting this value displays the dynamic option, **DestinationType**.|  
|**Variable**|Set the variable to store the results of the WQL query in. Selecting this value displays the dynamic option, **DestinationType**.|  
  
## WQLQuerySourceType Dynamic Options  
  
### WQLQuerySourceType \= Direct input  
 **WQLQuerySource**  
 Provide a query, or click the ellipsis \(…\) and enter a query using the **WQL Query** dialog box.  
  
### WQLQuerySourceType \= File connection  
 **WQLQuerySource**  
 Select a File connection manager in the list, or click \<**New connection...**\> to create a new connection manager.  
  
 **Related Topics:** [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md), [File Connection Manager Editor](../../Topics\TopicNameNotContainA/File-Connection-Manager-Editor.md)  
  
### WQLQuerySourceType \= Variable  
 **WQLQuerySource**  
 Select a variable in the list, or click \<**New variable...**\> to create a new variable.  
  
 **Related Topics:** [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md), [Add Variable](../../Topics\TopicNameNotContainA/Add-Variable.md)  
  
## DestinationType Dynamic Options  
  
### DestinationType \= File connection  
 **Destination**  
 Select a File connection manager in the list, or click \<**New connection...**\> to create a new connection manager.  
  
 **Related Topics:** [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md), [File Connection Manager Editor](../../Topics\TopicNameNotContainA/File-Connection-Manager-Editor.md)  
  
### DestinationType \= Variable  
 **Destination**  
 Select a variable in the list, or click \<**New variable...**\> to create a new variable.  
  
 **Related Topics:** [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md), [Add Variable](../../Topics\TopicNameNotContainA/Add-Variable.md)  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [WMI Data Reader Task Editor &#40;General Page&#41;](../Topic/WMI%20Data%20Reader%20Task%20Editor%20\(General%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)   
 [WMI Event Watcher Task](../../Topics\TopicNameNotContainA/WMI-Event-Watcher-Task.md)  
  
  