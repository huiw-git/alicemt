---
title: Specify Job Responses
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Specify Job Responses
Job responses specify actions that the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service will take after a job completes. Job responses ensure that database administrators know when jobs complete and how frequently they run. Typical job responses include:  
  
-   Notifying the operator by using e\-mail, electronic paging, or a **net send** message.  
  
    Use one of these job responses if the operator must perform a follow\-up action. For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.  
  
-   Writing an event message to the Windows application log.  
  
    You can use this response only for failed jobs.  
  
-   Automatically deleting the job.  
  
    Use this job response if you are certain that you do not need to rerun this job.  
  
## Related Tasks  
  
|||  
|-|-|  
|**Description**|**Topic**|  
|Describes how to notify an operator of job status.|[Notify an Operator of Job Status](../content/Notify-an-Operator-of-Job-Status.md)|  
|Describes how to write job status to the Windows application log.|[Write the Job Status to the Windows Application Log](../content/Write-the-Job-Status-to-the-Windows-Application-Log.md)|  
  
## See Also  
[Monitor and Respond to Events](../content/Monitor-and-Respond-to-Events.md)  
  
