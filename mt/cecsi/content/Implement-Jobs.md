---
title: "Implement Jobs"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 4
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
# Implement Jobs
You can use [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs to automate routine administrative tasks and run them on a recurring basis, making administration more efficient.  
  
A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent. A job can perform a wide range of activities, including running [!INCLUDE[tsql](../content/includes/tsql_md.md)] scripts, command-line applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks. Jobs can run repetitive tasks or those that can be scheduled, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] administration.  
  
You can run a job manually, or you can configure it to run according to a schedule or in response to alerts.  
  
## Related Tasks  
  
|||  
|-|-|  
|**Description**|**Topic**|  
|Contains information about creating jobs and assigning ownership.|[Create Jobs](../content/Create-Jobs.md)|  
|Contains information about organizing jobs into categories.|[Organize Jobs](../content/Organize-Jobs.md)|  
|Contains information about the different kinds of job steps you can create and how to manage them.|[Manage Job Steps](../content/Manage-Job-Steps.md)|  
|Contains information about how to define when jobs start running and how often they should run.|[Create and Attach Schedules to Jobs](../content/Create-and-Attach-Schedules-to-Jobs.md)|  
|Contains information about manually running jobs (without a schedule).|[Run Jobs](../content/Run-Jobs.md)|  
|Contains information about how you can configure [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to respond to jobs. For example, you can configure [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to notify administrators when jobs are finished.|[Specify Job Responses](../content/Specify-Job-Responses.md)|  
|Contains information about how to view existing jobs, their history once executes, and how to modify them.|[View or Modify Jobs](../content/View-or-Modify-Jobs.md)|  
|Contains information about how to delete jobs.|[Delete Jobs](../content/Delete-Jobs.md)|  
  
## See Also  
[Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md)  
  
