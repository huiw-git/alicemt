---
title: Modify a SQL Server Agent Proxy
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
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
# Modify a SQL Server Agent Proxy
This topic describes how to modify a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxy in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To modify a SQL Server Agent proxy, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxies use credentials to store information about Windows user accounts. The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is running.  
  
-   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs. If the proxy no longer has access to the subsystem, the job step fails. Otherwise, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.  
  
-   If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To modify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxy  
  
1.  In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxy account that you want to modify.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Click the plus sign to expand the **Proxies** folder.  
  
4.  Click the plus sign to expand the subsystem node for the proxy (for example, **ActiveX Script**).  
  
5.  Right\-click the proxy account you want to modify and select **Properties**.  
  
6.  In the *proxy\_name***Proxy Account Properties** dialog box, make changes to the proxy account as necessary. For more information on the options in this dialog box, see [Create a SQL Server Agent Proxy](../content/Create-a-SQL-Server-Agent-Proxy.md).  
  
7.  When finished, click **OK**.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To modify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxy  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
For more information, see [sp_update_proxy (Transact-SQL)](assetId:///864fd0e6-9d61-4f07-92ef-145318d2f881).  
  
