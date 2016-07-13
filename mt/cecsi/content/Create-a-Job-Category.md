---
title: Create a Job Category
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
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
# Create a Job Category
This topic describes how to create a job category in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], [!INCLUDE[tsql](../content/includes/tsql_md.md)] or [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Management Objects.  
  
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent provides built\-in job categories that you can assign jobs to, or you can create a job category and assign jobs to it. Job categories help you organize your jobs for easy filtering and grouping. For example, you can organize all your database backup jobs in the Database Maintenance category. You can also create your own job categories.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To create a job category, using:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
Multiserver categories exist only on a master server. There is only one default job category available on a master server: \[**Uncategorized (Multi\-Server)**]. When a multiserver job is downloaded, its category is changed to **Jobs From MSX** at the target server.  
  
### <a name="Security"></a>Security  
For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md).  
  
## <a name="SSMS"></a>Using SQL Server Management Studio  
  
#### To create a job category  
  
1.  In **Object Explorer**, click the plus sign to expand the server where you want to create a job category.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Right\-click the **Jobs** folder and select **Manage Job Categories**.  
  
4.  In the **Manage Job Categories***server\_name* dialog box, click **Add**.  
  
5.  In the new dialog box, in the **Name** box, enter a name for the new job category.  
  
6.  Select the **Show all jobs** check box. Select one or more jobs for the new category by checking the boxes corresponding to the jobs.  
  
7.  Click **OK**.  
  
8.  In the **Manage Job Categories***server\_name* dialog box, click **Refresh** to ensure that the new job category is active. If everything looks as expected, close this dialog box.  
  
For more information on these dialog boxes, see [Job Categories - Manage Job Categories](../content/Job-Categories---Manage-Job-Categories.md) and [Job Categories Properties - New Job Category](../content/Job-Categories-Properties---New-Job-Category.md).  
  
## <a name="TSQL"></a>Using Transact\-SQL  
  
#### To create a job category  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
For more information, see [sp_add_category (Transact-SQL)](assetId:///6cca32cd-d941-4378-aed6-a7c90cb7520a).  
  
## <a name="SMO"></a>Using SQL Server Management Objects  
**To create a job category**  
  
Call the **JobCategory** class by using a programming language that you choose, such as Visual Basic, Visual C\#, or PowerShell. For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](assetId:///900242ad-d6a2-48e9-8a1b-f0eea4413c16).  
  
