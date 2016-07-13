---
title: Create a WMI Event Alert
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
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
# Create a WMI Event Alert
This topic describes how to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent alert that is raised when a specific [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] event occurs that is monitored by the WMI Provider for Server Events in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
For information about the using the WMI Provider to monitor [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] events, see [WMI Provider for Server Events Classes and Properties](assetId:///80767fe0-32ac-406a-81a0-8212cd6ce7e4). For information about the permissions necessary to receive WMI event alert notifications, see [Select an Account for the SQL Server Agent Service](../content/Select-an-Account-for-the-SQL-Server-Agent-Service.md). For more information about WQL, see [Using WQL with the WMI Provider for Server Events](assetId:///58b67426-1e66-4445-8e2c-03182e94c4be).  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To create a WMI event alert, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.  
  
-   Events generated with **xp\_logevent** occur in the master database. Therefore, **xp\_logevent** does not trigger an alert unless the **@database\_name** for the alert is **'master'** or NULL.  
  
-   Only WMI namespaces on the computer that runs [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent are supported.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
By default, only members of the **sysadmin** fixed server role can execute **sp\_add\_alert**.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To create a WMI event alert  
  
1.  In **Object Explorer,** click the plus sign to expand the server where you want to create a WMI event alert.  
  
2.  Click the plus sign to expand **SQL Server Agent**.  
  
3.  Right\-click **Alerts** and select **New Alert**.  
  
4.  In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.  
  
5.  Check the **Enable** check box to enable the alert to run. By default, **Enable** is checked.  
  
6.  In the **Type** list, select **WMI event alert**.  
  
7.  Under **WMI event alert definition**, in the **Namespace** box, specify the WMI namespace for the WMI Query Language (WQL) statement that identifies which WMI event will trigger this alert.  
  
8.  In the **Query** box, specify the WQL statement that identifies the event that this alert responds to.  
  
9. Click **OK**.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To create a WMI event alert  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database. Please see the following information…',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
For more information, see [sp_add_alert (Transact-SQL)](assetId:///d9b41853-e22d-4813-a79f-57efb4511f09).  
  
