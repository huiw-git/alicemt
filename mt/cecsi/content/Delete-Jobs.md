---
title: Delete Jobs
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
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
# Delete Jobs
A job is a specified series of operations performed sequentially by SQL Server Agent. By default, jobs are not deleted when execution finishes. You can delete one or more [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs regardless of success or failure of the job. You can also configure [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.  
  
By default, members of the **sysadmin** fixed server role can execute the [sp_delete_job (Transact-SQL)](assetId:///b85db6e4-623c-41f1-9643-07e5ea38db09) system stored procedure to delete a job. Other users must be granted one of the following [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database roles in the **msdb** database:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](../content/SQL-Server-Agent-Fixed-Database-Roles.md).  
  
Members of the **sysadmin** fixed server role can execute **sp\_delete\_job** to delete any job. A user that is not a member of the **sysadmin** fixed server role can only delete jobs owned by that user.  
  
## Related Tasks  
  
|||  
|-|-|  
|**Description**|**Topic**|  
|Describes how to delete one or more [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs.|[Delete One or More Jobs](../content/Delete-One-or-More-Jobs.md)|  
|Describes how to configure [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.|[Automatically Delete a Job](../content/Automatically-Delete-a-Job.md)|  
  
