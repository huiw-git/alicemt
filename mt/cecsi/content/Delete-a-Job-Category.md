---
title: Delete a Job Category
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
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
# Delete a Job Category
This topic describes how to delete a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent job category in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], [!INCLUDE[tsql](../content/includes/tsql_md.md)] or SQL Server Management Objects.  
  
Job categories help you organize your jobs for easy filtering and grouping. For example, you can organize all your database backup jobs in the Database Maintenance category.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To delete a job category, using:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
When you delete a user\-defined job category, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent prompts you to reassign the jobs that are assigned to it to another job category. You can only delete user\-defined job categories.  
  
### <a name="Security"></a>Security  
For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md).  
  
## <a name="SSMS"></a>Using SQL Server Management Studio  
  
#### To delete a job category  
  
1.  In **Object Explorer**, click the plus sign to expand the server where you want to delete a job category.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Right\-click the **Jobs** folder and select **Manage Job Categories**.  
  
4.  In the **Manage Job Categories***server\_name* dialog box, select the job category to delete.  
  
5.  Click **Delete**.  
  
6.  In the **Job Categories** dialog box, click **Yes**.  
  
7.  Close the **Manage Job Categories***server\_name* dialog box.  
  
## <a name="TSQL"></a>Using Transact\-SQL  
  
#### To delete a job category  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
For more information, see [sp_delete_category (Transact-SQL)](assetId:///63ea7d0d-a567-456e-a778-bee99e21d16c).  
  
## <a name="SMO"></a>Using SQL Server Management Objects  
**To delete a job category**  
  
Call the **JobCategory** class by using a programming language that you choose, such as Visual Basic, Visual C\#, or PowerShell.  
  
