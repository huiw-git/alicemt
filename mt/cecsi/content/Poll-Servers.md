---
title: Poll Servers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
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
# Poll Servers
When multiserver administration is implemented, target servers periodically contact the master server to upload information on jobs that have been executed, and download new jobs. The process of contacting the master server is called *server polling,* which takes place at regular *polling intervals.*  
  
## Polling Intervals  
The polling interval (one minute by default) controls how frequently the target server connects to the master server to download instructions and upload the results of job execution.  
  
When a target server polls the master server, it reads the operations assigned to the target server from the **sysdownloadlist** table in the **msdb** database. These operations control multiserver jobs and various aspects of the behavior of a target server. Examples of operations include deleting a job, inserting a job, starting a job, and updating the polling interval of a target server.  
  
Operations are posted to the **sysdownloadlist** table in either of the following ways:  
  
-   Explicitly by using the **sp\_post\_msx\_operation** stored procedure.  
  
-   Implicitly by using other job stored procedures.  
  
If you use job stored procedures to modify multiserver job schedules or job steps, or SQL Distributed Management Objects (SQL\-DMO) to control multiserver jobs, issue the following command after modifying a multiserver job's steps or schedules:  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Issue this command keeps the target servers synchronized with the current job definition.  
  
You do not have to post operations explicitly if you use the following:  
  
-   Microsoft [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] to control multiserver jobs.  
  
-   Job stored procedures that do not modify job schedules or job steps.  
  
**To force a target server to poll the master server**  
  
-   [SQL Server Management Studio](../content/Force-a-Target-Server-to-Poll-the-Master-Server.md)  
  
-   [Transact-SQL](assetId:///085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## See Also  
[Manage Events](../content/Manage-Events.md)  
  
