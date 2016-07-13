---
title: View or Modify Jobs
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
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
# View or Modify Jobs
You can view any job you have created. After you have run a job, you can also view its history. Viewing a job's history allows you to see when the job ran, the status of the job as a whole, and the status of each job step in the job. You can see whether the job ever failed in the past, when the job last completed successfully, and what output the job created each time the job ran. Members of the **sysadmin** fixed server role can view or modify any job, regardless of the owner.  
  
> [!NOTE]  
> A job must have been executed at least one time for there to be a job history. You can limit the total size of the job history log and the size per job.  
  
Finally, you can modify a job to meet new requirements. You can modify:  
  
-   Response options  
  
-   Schedules  
  
-   Job steps  
  
-   Ownership  
  
-   Job category  
  
-   Target servers (multiserver jobs only)  
  
To make sure that changes to multiserver jobs take effect, you must post the changes to the download list so that target servers can download the updated job. To ensure that target servers have the most current job definitions, post an INSERT instruction after you update the multiserver job as follows:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
For more information, see [sp_purge_jobhistory (Transact-SQL)](assetId:///237f9bad-636d-4262-9bfb-66c034a43e88).  
  
Members of the **sysadmin** fixed server role can view the definition or history of any job, and can modify any job.  
  
## Related Tasks  
  
|||  
|-|-|  
|**Description**|**Topic**|  
|Describes how to view [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs.|[View a Job](../content/View-a-Job.md)|  
|Describes how to view the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent job history log.|[View the Job History](../content/View-the-Job-History.md)|  
|Describes how to delete the contents of the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent job history log.|[Clear the Job History Log](../content/Clear-the-Job-History-Log.md)|  
|Describes how to set size limits for [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent job history logs.|[Resize the Job History Log](../content/Resize-the-Job-History-Log.md)|  
|Describes how to change the properties of [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs.|[Modify a Job](../content/Modify-a-Job.md)|  
  
## See Also  
[sysjobhistory](assetId:///1b1fcdbb-2af2-45e6-bf3f-e8279432ce13)  
  
