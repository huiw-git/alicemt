---
title: Delete a SQL Server Agent Proxy
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
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
# Delete a SQL Server Agent Proxy
This topic describes how to delete a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxy account in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To delete a SQL Server Agent proxy account, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   When you delete a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxy account, make sure the proxy does not reference any active job steps. To check for any job steps that reference the proxy, right\-click the proxy, select **Properties**, and then, in the *proxy\_name***Proxy Account Properties** dialog box, select the **References** page. If you delete a proxy, you are given the option to reassign all job steps that use that proxy in the **Delete Object** dialog box.  
  
-   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxies use credentials to store information about Windows user accounts. The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is running.  
  
-   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs. If the proxy no longer has access to the subsystem, the job step fails. Otherwise, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.  
  
-   If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To delete a SQL Server Agent proxy account  
  
1.  In **Object Explorer**, click the plus sign to expand a server that contains the proxy account that you want to delete.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Click the plus sign to expand the **Proxies** folder.  
  
4.  Click the plus sign to expand the subsystem that contains the proxy account you want to delete (for example, **ActiveX Script)**.  
  
5.  Right\-click the proxy account that you want to delete and select **Delete**.  
  
6.  In the **Delete Object** dialog box, confirm that the correct proxy account is selected. Check the **Reassign to** check box to reassign the job steps that reference this proxy account to another account.  
  
7.  Click **OK**.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To delete a SQL Server Agent proxy account  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
For more information, see [sp_delete_proxy (Transact-SQL)](assetId:///44a1db13-b7f2-4dab-a1b5-b8dafb41737c).  
  
