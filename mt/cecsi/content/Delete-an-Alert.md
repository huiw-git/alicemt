---
title: Delete an Alert
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c982b208-e2d1-4d34-8cee-940b9baf6586
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
# Delete an Alert
This topic describes how to delete [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent alerts in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To delete an alert, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
Removing an alert also removes any notifications associated with the alert.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
By default, only members of the **sysadmin** fixed server role can delete alerts.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To delete an alert  
  
1.  In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent alert that you want to delete.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Click the plus sign to expand the **Alerts** folder.  
  
4.  Right\-click the alert you want to delete and select **Delete**.  
  
5.  In the **Delete Object** dialog box, confirm that the correct alert is selected and click **OK**.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To delete an alert  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- deletes the SQL Server Agent alert called 'Test Alert.'  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_alert  
       @name = N'Test Alert' ;  
    GO  
    ```  
  
For more information, see [sp_delete_alert (Transact-SQL)](assetId:///a831315e-793d-41c4-8333-b324bb2bc614).  
  
