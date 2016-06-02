---
title: Integration Services Containers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b725922-ec59-4a47-9d55-e079463058f3
---
# Integration Services Containers
  Containers are objects in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] that provide structure to packages and services to tasks. They support repeating control flows in packages, and they group tasks and containers into meaningful units of work. Containers can include other containers in addition to tasks.  
  
 Packages use containers for the following purposes:  
  
-   Repeat tasks for each element in a collection, such as files in a folder, schemas, or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Objects \(SMO\) objects. For example, a package can run Transact\-SQL statements that reside in multiple files.  
  
-   Repeat tasks until a specified expression evaluates to **false**. For example, a package can send a different e\-mail message seven times, one time for every day of the week.  
  
-   Group tasks and containers that must succeed or fail as a unit. For example, a package can group tasks that delete and add rows in a database table, and then commit or roll back all the tasks when one fails.  
  
## Container Types  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides four types of containers for building packages. The following table lists the container types.  
  
|Container|Description|  
|---------------|-----------------|  
|[Foreach Loop Container](../../Topics\TopicNameNotContainA/Foreach-Loop-Container.md)|Runs a control flow repeatedly by using an enumerator.|  
|[For Loop Container](../../Topics\TopicNameNotContainA/For-Loop-Container.md)|Runs a control flow repeatedly by testing a condition.|  
|[Sequence Container](../../Topics\TopicNameNotContainA/Sequence-Container.md)|Groups tasks and containers into control flows that are subsets of the package control flow.|  
|[Task Host Container](../../Topics\TopicNameNotContainA/Task-Host-Container.md)|Provides services to a single task.|  
  
 Packages and events handlers are also types of containers. For information see [Integration Services &#40;SSIS&#41; Packages](../Topic/Integration%20Services%20\(SSIS\)%20Packages.md) and [Integration Services &#40;SSIS&#41; Event Handlers](../Topic/Integration%20Services%20\(SSIS\)%20Event%20Handlers.md).  
  
### Summary of Container Properties  
 All container types have a set of properties in common. If you create packages using the graphical tools that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides, the Properties window lists the following properties for the Foreach Loop, For Loop, and Sequence containers. The task host container properties are configured as part of configuring the task that the task host encapsulates. You set the Task Host properties when you configure the task.  
  
|Property|Description|  
|--------------|-----------------|  
|**DelayValidation**|A Boolean value that indicates whether validation of the container is delayed until run time. The default value for this property is **False**.<br /><br /> For more information, see [DelayValidation](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation).|  
|**Description**|The container description. The property contains a string, but may be blank.<br /><br /> For more information, see [Description](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description).|  
|**Disable**|A Boolean value that indicates whether the container runs. The default value for this property is **False**.<br /><br /> For more information, see [Disable](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable).|  
|**DisableEventHandlers**|A Boolean value that indicates whether the event handlers associated with the container run. The default value for this property is **False**.|  
|**FailPackageOnFailure**|A Boolean value that specifies whether the package fails if an error occurs in the container. The default value for this property is **False**.<br /><br /> For more information, see [FailPackageOnFailure](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure).|  
|**FailParentOnFailure**|A Boolean value that specifies whether the parent container fails if an error occurs in the container. The default value for this property is **False**.<br /><br /> For more information, see [FailParentOnFailure](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure).|  
|**ForcedExecutionValue**|If **ForceExecutionValue** is set to **True**, the object that contains the optional execution value for the container. The default value of this property is **0**.<br /><br /> For more information, see [ForcedExecutionValue](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue).|  
|**ForcedExecutionValueType**|The data type of **ForcedExecutionValue**. The default value of this property is **Int32**.|  
|**ForceExecutionResult**|A value that specifies the forced result of running the package or container. The values are **None**, **Success**, **Failure**, and **Completion**. The default value for this property is **None**.<br /><br /> For more information, see [ForceExecutionResult](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult).|  
|**ForceExecutionValue**|A Boolean value that specifies whether the optional execution value of the container should be forced to contain a particular value. The default value of this property is **False**.<br /><br /> For more information, see [ForceExecutionValue](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue).|  
|**ID**|The container GUID, which is assigned when the package is created. This property is read\-only.<br /><br /> [ID](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID).|  
|**IsolationLevel**|The isolation level of the container transaction. The values are **Unspecified**, **Chaos**, **ReadUncommitted**, **ReadCommitted**, **RepeatableRead**, **Serializable**, and **Snapshot**. The default value of this property is **Serializable**. For more information, see [IsolationLevel](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel).|  
|**LocaleID**|A Microsoft Win32 locale. The default value of this property is the locale of the operating system on the local computer.<br /><br /> For more information, see [LocaleID](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID).|  
|**LoggingMode**|A value that specifies the logging behavior of the container. The values are **Disabled**, **Enabled**, and **UseParentSetting**. The default value of this property is **UseParentSetting**. For more information, see [DTSLoggingMode](assetId:///T:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode).|  
|**MaximumErrorCount**|The maximum number of errors that can occur before a container stops running. The default value of this property is **1**.<br /><br /> For more information, see [MaximumErrorCount](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount).|  
|**Name**|The name of the container.<br /><br /> For more information, see [Name](assetId:///P:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name).|  
|**TransactionOption**|The transactional participation of the container. The values are **NotSupported**, **Supported**, **Required**. The default value of this property is **Supported**. For more information, see [DTSTransactionOption](assetId:///T:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption).|  
  
 To learn about all the properties that are available to Foreach Loop, For Loop, Sequence, and Task Host containers when configure them programmatically, see the following [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] API topics:  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.Sequence  
  
-   T:Microsoft.SqlServer.Dts.Runtime.TaskHost  
  
## Objects that Extend Container Functionality  
 Containers include control flows that consist of executables and precedence constraints, and may use event handlers, and variables. The task host container is an exception: because the task host container encapsulates a single task, it does not use precedence constraints.  
  
### Executables  
 Executables refers to the container\-level tasks and any containers within the container. An executable can be one of the tasks and containers that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides or a custom task. For more information, see [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md).  
  
### Precedence Constraints  
 Precedence constraints link containers and tasks within the same parent container into an ordered control flow. For more information, see [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md).  
  
### Event Handlers  
 Event handlers at the container level respond to events raised by the container or the objects it includes. For more information, see [Integration Services &#40;SSIS&#41; Event Handlers](../Topic/Integration%20Services%20\(SSIS\)%20Event%20Handlers.md).  
  
### Variables  
 Variables that are used in containers include the container\-level system variables that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides and the user\-defined variables that the container uses. For more information, see [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md).  
  
## Break Points  
 When you set a breakpoint on a container and the break condition is **Break when the container recevies the OnVariableValueChanged event**, define the variable in the container scope.  
  
## See Also  
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  