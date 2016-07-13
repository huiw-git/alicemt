---
title: Change the Scheduling Details for a SQL Server Agent Master Job
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5414451-4d8e-464b-bd9e-f2b70c6899b3
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
# Change the Scheduling Details for a SQL Server Agent Master Job
This topic describes how to change the scheduling details for a job definition in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To change the scheduling details for a job definition, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
A [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent master job cannot be targeted at both local and remote servers.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own. For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md).  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To change the scheduling details for a job definition  
  
1.  In **Object Explorer,** click the plus sign to expand the server that contains the job whose schedule you want to edit.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Click the plus sign to expand the **Jobs** folder.  
  
4.  Right\-click the job whose schedule you want to edit and select **Properties**.  
  
5.  In the **Job Properties –***job\_name* dialog box, under **Select a page**, select **Schedules**. For more information on the available options on this page, see [Job Properties - New Job &#40;Schedules Page&#41;](../content/Job-Properties---New-Job--Schedules-Page-.md).  
  
6.  When finished, click **OK**.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To change the scheduling details for a job definition  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- changes the enabled status of the NightlyJobs schedule to 0   
    -- and sets the owner to terrid.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_schedule  
        @name = 'NightlyJobs',  
        @enabled = 0,  
        @owner_login_name = 'terrid' ;  
    GO  
    ```  
  
For more information, see [sp_update_schedule (Transact-SQL)](assetId:///97b3119b-e43e-447a-bbfb-0b5499e2fefe).  
  
