---
title: View Information About an Operator
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
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
# View Information About an Operator
This topic describes how to view information about a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent operator in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To view information about an operator, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
By default, members of the **sysadmin** fixed server role can execute this stored procedure. Other users must be granted one of the following [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database roles in the **msdb** database:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](../content/SQL-Server-Agent-Fixed-Database-Roles.md).  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To view information about an operator  
  
1.  In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to view.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Click the plus sign to expand the **Operators** folder.  
  
4.  Right\-click the operator that you want to view and select **Properties**.  
  
    For more information on the available options contained in the *operator\_name***Properties** dialog box, see:  
  
    -   [Operator Properties - New Operator &#40;General Page&#41;](../content/Operator-Properties---New-Operator--General-Page-.md)  
  
    -   [Operator Properties - New Operator &#40;Notifications Page&#41;](../content/Operator-Properties---New-Operator--Notifications-Page-.md)  
  
    -   [Operator Properties &#40;History Page&#41;](../content/Operator-Properties--History-Page-.md)  
  
5.  When finished, click **OK**.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To view information about an operator  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- reports information about operator François Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'François Ajenstat' ;  
    GO  
    ```  
  
For more information, see [sp_help_operator (Transact-SQL)](assetId:///caedc43d-44b8-415a-897e-92923f6de3b8).  
  
