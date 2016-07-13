---
title: View Job Activity
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
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
# View Job Activity
This topic describes how to view the runtime state of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
When the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service starts, a new session is created and the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs. This table records current job activity and status. You can use the Job Activity Monitor in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to view the current state of jobs. If the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service unexpectedly terminates, you can refer to the **sysjobactivity** table to see which jobs were being executed when the service terminated.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To view job activity, using:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
## Before You Begin  
  
### <a name="Security"></a>Security  
For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md).  
  
## <a name="SSMS"></a>Using SQL Server Management Studio  
  
#### To view job activity  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **SQL Server Agent**.  
  
3.  Right\-click **Job Activity Monitor** and click **View Job Activity**.  
  
4.  In the **Job Activity Monitor**, you can view details about each job that is defined for this server.  
  
5.  Right\-click a job to start it, stop it, enable or disable it, refresh its status as displayed in the Job Activity Monitor, delete it, or view its history or properties.  To start, stop, enable or disable, or refresh multiple jobs, select multiple rows in the Job Activity Monitor, and right\-click your selection.  
  
6.  To update the Job Activity Monitor, click **Refresh**. To view fewer rows, click **Filter** and enter filter parameters.  
  
## <a name="TSQL"></a>Using Transact\-SQL  
  
#### To view job activity  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
For more information, see [sp_help_jobactivity (Transact-SQL)](assetId:///d344864f-b4d3-46b1-8933-b81dec71f511).  
  
