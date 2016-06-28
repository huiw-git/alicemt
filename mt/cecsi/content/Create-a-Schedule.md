---
title: Create a Schedule
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
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
# Create a Schedule
You can create a schedule for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent jobs in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], [!INCLUDE[tsql](../content/includes/tsql_md.md)], or SQL Server Management Objects.  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To create a schedule, using:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md).  
  
## <a name="SSMS"></a>Using SQL Server Management Studio  
  
#### To create a schedule  
  
1.  In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **SQL Server Agent**, right\-click **Jobs**, and select **Manage Schedules**.  
  
3.  In the **Manage Schedules** dialog box, click **New**.  
  
4.  In the **Name** box, type a name for the new schedule.  
  
5.  If you do not want the schedule to take effect immediately after it has been created, clear the **Enabled** check box.  
  
6.  For **Schedule Type**, select one of the following:  
  
    -   To start the job when the CPUs reach an idle condition, click **Start whenever the CPUs become idle**.  
  
    -   If you want a schedule to run repeatedly, click **Recurring**. To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.  
  
    -   If you want the schedule to run only one time, click **One time**. To set the **One time** schedule, complete the **One\-time occurrence** group on the dialog box.  
  
## <a name="TSQL"></a>Using Transact\-SQL  
  
#### To create a schedule  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
For more information, see [sp_add_schedule (Transact-SQL)](assetId:///9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7).  
  
## <a name="SMO"></a>Using SQL Server Management Objects  
**To create a schedule**  
  
Use the **JobSchedule** class by using a programming language that you choose, such as Visual Basic, Visual C\#, or PowerShell. For more information, see [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
