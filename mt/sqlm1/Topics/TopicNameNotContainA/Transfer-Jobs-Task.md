---
title: Transfer Jobs Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
---
# Transfer Jobs Task
  The Transfer Jobs task transfers one or more [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent jobs between instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 The Transfer Jobs task can be configured to transfer all jobs, or only specified jobs. You can also indicate whether the transferred jobs are enabled at the destination.  
  
 The jobs to be transferred may already exist on the destination. The Transfer Jobs task can be configured to handle existing jobs in the following ways:  
  
-   Overwrite existing jobs.  
  
-   Fail the task when duplicate jobs exist.  
  
-   Skip duplicate jobs.  
  
 At run time, the Transfer Jobs task connects to the source and destination servers by using one or two SMO connection managers. The SMO connection manager is configured separately from the Transfer Jobs task, and then is referenced in the Transfer Jobs task. The SMO connection manager specifies the server and the authentication mode to use when accessing the server. For more information, see [SMO Connection Manager](../../Topics\TopicNameNotContainA/SMO-Connection-Manager.md).  
  
## Transferring Jobs Between Instances of SQL Server  
 The Transfer Jobs task supports a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] source and destination. There are no restrictions on which version to use as a source or destination.  
  
## Events  
 The Transfer Jobs task raises an information event that reports the number of jobs transferred and a warning event when a job is overwritten. The task does not report incremental progress of the job transfer; it reports only 0% and 100% completion.  
  
## Execution Value  
 The execution value, defined in the **ExecutionValue** property of the task, returns the number of jobs that are transferred. By assigning a user\-defined variable to the **ExecValueVariable** property of the Transfer Jobs task, information about the job transfer can be made available to other objects in the package. For more information, see [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md) and [Use Variables in Packages](../../Topics\TopicNameNotContainA/Use-Variables-in-Packages.md).  
  
## Log Entries  
 The Transfer Jobs task includes the following custom log entries:  
  
-   TransferJobsTaskStarTransferringObjects   This log entry reports that the transfer has started. The log entry includes the start time.  
  
-   TransferJobsTaskFinishedTransferringObjects    This log entry reports that the transfer has finished. The log entry includes the end time.  
  
 In addition, a log entry for the **OnInformation** event reports the number of jobs that were transferred and a log entry for the **OnWarning** event is written for each job on the destination that is overwritten.  
  
## Security and Permissions  
 To transfer jobs, the user must be a member of the sysadmin fixed server role or one of the fixed [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent fixed database roles on the msdb database on the both the source and destination instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## Configuration of the Transfer Jobs Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [Transfer Jobs Task Editor &#40;General Page&#41;](../Topic/Transfer%20Jobs%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Transfer Jobs Task Editor &#40;Jobs Page&#41;](../Topic/Transfer%20Jobs%20Task%20Editor%20\(Jobs%20Page\).md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For information about programmatically setting these properties, click the of the following topic:  
  
-   [TransferJobsTask](assetId:///T:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask)  
  
## Related Tasks  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  