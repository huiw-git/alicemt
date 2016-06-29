---
title: Manage Jobs Across an Enterprise
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
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
# Manage Jobs Across an Enterprise
If you make changes to multiserver job definitions outside [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], you must post the changes to the download list so that target servers can download the updated job again. To ensure that target servers have current job definitions, post an INSERT instruction after you update the multiserver job, as follows:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
To notify target servers that a multiserver job has been modified, you must invoke the preceding command after using any of the following procedures:  
  
-   [sp_add_jobstep (Transact-SQL)](assetId:///97900032-523d-49d6-9865-2734fba1c755)  
  
-   [sp_update_jobstep (Transact-SQL)](assetId:///e158802c-c347-4a5d-bf75-c03e5ae56e6b)  
  
-   [sp_delete_jobstep (Transact-SQL)](assetId:///421ede8e-ad57-474a-9fb9-92f70a3e77e3)  
  
-   [Managing Events](assetId:///80c80eaf-cf23-4ed8-b8dd-65fe59830dd1)  
  
-   [sp_detach_schedule (Transact-SQL)](assetId:///9a1fc335-1bef-4638-a33a-771c54a5dd19)  
  
    > [!NOTE]  
    > It is not necessary to call **sp\_post\_msx\_operation** after you call **sp\_update\_job** or **sp\_delete\_job**, because these stored procedures post the required changes to the download list automatically.  
  
The following are common tasks for managing jobs across an enterprise:  
  
**To check the status of a target server**  
  
-   [Transact-SQL](assetId:///f841d3bd-901a-4980-ad0b-1c6eeba3f717)  
  
-   [SQL Server Management Objects (SMO)](assetId:///4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**To change the target servers for a job**  
  
-   [SQL Server Management Studio](../content/Modify-the-Target-Servers-for-a-Job.md)  
  
-   [Transact-SQL](assetId:///485252cc-0081-490a-9bd1-cbbd68eea286)  
  
-   [SQL Server Management Objects (SMO)](assetId:///4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**To change the location of a target server**  
  
-   [SQL Server Management Studio](../content/Specify-a-Target-Server-s-Location--SQL-Server-Management-Studio-.md)  
  
-   [Transact-SQL](assetId:///ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f)  
  
-   [SQL Server Management Objects (SMO)](assetId:///4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**To synchronize target server clocks**  
  
-   [SQL Server Management Studio](../content/Synchronize-Target-Server-Clocks--SQL-Server-Management-Studio-.md)  
  
-   [Transact-SQL](assetId:///40e44df7-d3e3-44ee-b149-08aba629a21f)  
  
**To force a target server to poll the master server**  
  
-   [SQL Server Management Studio](../content/Force-a-Target-Server-to-Poll-the-Master-Server.md)  
  
-   [Transact-SQL](assetId:///085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## See Also  
[Manage Events](../content/Manage-Events.md)  
  
