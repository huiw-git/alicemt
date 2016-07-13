---
title: Create Jobs
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
manager:jhubbard
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
# Create Jobs
A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent. A job can perform a wide range of activities, including running [!INCLUDE[tsql](../content/includes/tsql_md.md)] scripts, command prompt applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks. Jobs can run repetitive or schedulable tasks, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] administration.  
  
To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database roles or the **sysadmin** fixed server role. A job can be edited only by its owner or members of the **sysadmin** role. Members of the **sysadmin** role can assign job ownership to other users, and they can run any job, regardless of the job owner. For more information about the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](../content/SQL-Server-Agent-Fixed-Database-Roles.md).  
  
Jobs can be written to run on the local instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or on multiple instances across an enterprise. To run jobs on multiple servers, you must set up at least one master server and one or more target servers. For more information about master and target servers, see [Automated Administration Across an Enterprise](../content/Automated-Administration-Across-an-Enterprise.md)  
  
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent records job and job step information in the job history.  
  
## Related Tasks  
  
|||  
|-|-|  
|**Description**|**Topic**|  
|Describes how to create a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent job.|[Create a Job](../content/Create-a-Job.md)|  
|Describes how to reassign ownership of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs to another user.|[Give Others Ownership of a Job](../content/Give-Others-Ownership-of-a-Job.md)|  
|Describes how to set up the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent job history log.|[Set Up the Job History Log](../content/Set-Up-the-Job-History-Log.md)|  
  
## See Also  
[Manage Job Steps](../content/Manage-Job-Steps.md)  
[Automated Administration Across an Enterprise](../content/Automated-Administration-Across-an-Enterprise.md)  
[Create and Attach Schedules to Jobs](../content/Create-and-Attach-Schedules-to-Jobs.md)  
[Run Jobs](../content/Run-Jobs.md)  
[View or Modify Jobs](../content/View-or-Modify-Jobs.md)  
  
