---
title: Create a Transact-SQL Job Step
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
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
# Create a Transact-SQL Job Step
This topic describes how to create a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent job step that executes [!INCLUDE[tsql](../content/includes/tsql_md.md)] scripts in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], [!INCLUDE[tsql](../content/includes/tsql_md.md)], or SQL Server Management Objects.  
  
These job step scripts may call stored procedures and extended stored procedures. A single [!INCLUDE[tsql](../content/includes/tsql_md.md)] job step can contain multiple batches and embedded GO commands. For more information on creating a job, see [Creating Jobs](../content/Create-Jobs.md).  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To create a Transact\-SQL job step, using:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md).  
  
## <a name="SSMS"></a>Using SQL Server Management Studio  
  
#### To create a Transact\-SQL job step  
  
1.  In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **SQL Server Agent**, create a new job or right\-click an existing job, and then click **Properties**.  
  
3.  In the **Job Properties** dialog, click the **Steps** page, and then click **New**.  
  
4.  In the **New Job Step** dialog, type a job **Step name**.  
  
5.  In the **Type** list, click **Transact\-SQL Script (TSQL)**.  
  
6.  In the **Command** box, type the [!INCLUDE[tsql](../content/includes/tsql_md.md)] command batches, or click **Open** to select a [!INCLUDE[tsql](../content/includes/tsql_md.md)] file to use as the command.  
  
7.  Click **Parse** to check your syntax.  
  
8.  The message "Parse succeeded" is displayed when your syntax is correct. If an error is found, correct the syntax before continuing.  
  
9. Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent should try to execute the job step, and the file or table where [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent can write the job step output. Only members of the **sysadmin** fixed server role can write job step output to an operating system file. All SQL Server Agent users can log output to a table.  
  
10. If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.  
  
## <a name="TSQL"></a>Using Transact\-SQL  
  
#### To create a Transact\-SQL job step  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- creates a job step that that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
For more information, see [sp_add_jobstep (Transact-SQL)](assetId:///97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Using SQL Server Management Objects  
**To create a Transact\-SQL job step**  
  
Use the **JobStep** class by using a programming language that you choose, such as Visual Basic, Visual C\#, or PowerShell.  
  
