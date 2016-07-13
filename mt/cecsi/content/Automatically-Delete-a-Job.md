---
title: Automatically Delete a Job
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92dbb6da-5919-4bde-9354-d454e9ea3da0
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
# Automatically Delete a Job
This topic describes how to configure [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] to automatically delete jobs when they succeed, fail, or complete by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or SQL Server Management Objects.  
  
Job responses ensure that database administrators know when jobs complete and how frequently they run. Typical job responses include:  
  
-   Notifying the operator by using e\-mail, electronic paging, or a **net send** message.  
  
    Use one of these job responses if the operator must perform a follow\-up action. For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.  
  
-   Writing an event message to the Windows application log.  
  
    You can use this response only for failed jobs.  
  
-   Automatically deleting the job.  
  
    Use this job response if you are certain that you do not need to rerun this job.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To specify job responses, using:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md).  
  
## <a name="SSMS"></a>Using SQL Server Management Studio  
  
#### To automatically delete a job  
  
1.  In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **SQL Server Agent**, expand **Jobs**, right\-click the job you want to edit, and then click **Properties**.  
  
3.  Select the **Notifications** page.  
  
4.  Check **Automatically delete job**, and choose one of the following:  
  
    -   Click **When the job succeeds** to delete the job status when it has completed successfully.  
  
    -   Click **When the job fails** to delete the job when it has completed unsuccessfully.  
  
    -   Click **When the job completes** to delete the job regardless of completion status.  
  
## <a name="SMO"></a>Using SQL Server Management Objects  
**To automatically delete a job**  
  
Use the **DeleteLevel** property of the **Job** class by using a programming language that you choose, such as Visual Basic, Visual C\#, or PowerShell. For more information, see [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
