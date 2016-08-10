---
title: "Delete or Disable DML Triggers"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-dml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# Delete or Disable DML Triggers
This topic describes how to delete or disable a DML trigger in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To delete or disable a DML trigger, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   When a trigger is deleted, it is dropped from the current database. The table and the data upon which it is based are not affected. Deleting a table automatically deletes any triggers on the table.  
  
-   A trigger is enabled by default when it is created.  
  
-   Disabling a trigger does not drop it. The trigger still exists as an object in the current database. However, the trigger will not fire when any INSERT, UPDATE, or DELETE statement on which it was programmed is executed. Triggers that are disabled can be reenabled. Enabling a trigger does not re-create it. The trigger fires in the same manner as when it was originally created.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 To delete a DML trigger requires ALTER permission on the table or view on which the trigger is defined.  
  
 To disable or enable a DML trigger, at a minimum, a user must have ALTER permission on the table or view on which the trigger was created.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To delete a DML trigger  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to delete.  
  
3.  Expand **Triggers**, right-click the trigger to delete, and then click **Delete**.  
  
4.  In the **Delete Object** dialog box, verify the trigger to delete, and then click **OK**.  
  
#### To disable and enable a DML trigger  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to disable.  
  
3.  Expand **Triggers**, right-click the trigger to disable, and then click **Disable**.  
  
4.  To enable the trigger, click **Enable**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To delete a DML trigger  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following examples into the query window. Execute the [CREATE TRIGGER](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7) statement to create the `Sales.bonus_reminder` trigger. To delete the trigger, execute the [DROP TRIGGER](assetId:///092d0d71-9f1e-4e38-a1c4-2487adfa5b4e) statement.  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### To disable and enable a DML trigger  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following examples into the query window. Execute the [CREATE TRIGGER](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7) statement to create the `Sales.bonus_reminder` trigger. To disable and enable the trigger, execute the [DISABLE TRIGGER](assetId:///e6529f06-e442-437e-a7bf-41790bc092c5) and [ENABLE TRIGGER](assetId:///6e21f0ad-68d0-432f-9c7c-a119dd2d3fc9) statements, respectively.  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```tsql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## See Also  
 [ALTER TRIGGER (Transact-SQL)](assetId:///2a99c7c1-ac2f-4637-aa7c-3d1bf514e500)   
 [CREATE TRIGGER (Transact-SQL)](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7)   
 [DROP TRIGGER (Transact-SQL)](assetId:///092d0d71-9f1e-4e38-a1c4-2487adfa5b4e)   
 [ENABLE TRIGGER (Transact-SQL)](assetId:///6e21f0ad-68d0-432f-9c7c-a119dd2d3fc9)   
 [DISABLE TRIGGER (Transact-SQL)](assetId:///e6529f06-e442-437e-a7bf-41790bc092c5)   
 [eventdata (Transact-SQL)](assetId:///03a80e63-6f37-4b49-bf13-dc35cfe46c44)   
 [Get Information About DML Triggers](../../Topics/TopicNameNotContainA/Get-Information-About-DML-Triggers.md)   
 [sp_help (Transact-SQL)](assetId:///913cd5d4-39a3-4a4b-a926-75ed32878884)   
 [sp_helptrigger (Transact-SQL)](assetId:///e486d39b-771d-488d-a786-7136433a2203)   
 [sys.triggers (Transact-SQL)](assetId:///cefa4fc4-b8b9-4cd7-b124-eed5283acbfc)   
 [sys.trigger_events (Transact-SQL)](assetId:///92540447-131c-491c-b033-c064c7d950e1)   
 [sys.sql_modules (Transact-SQL)](assetId:///23d3ccd2-f356-4d89-a2cd-bee381243f99)   
 [sys.assembly_modules (Transact-SQL)](assetId:///5f9e644e-8065-49a2-b53d-db7df98f70d8)   
 [sys.server_triggers (Transact-SQL)](assetId:///25926ff4-9271-45bf-bc32-d5d3344bd47a)   
 [sys.server_trigger_events (Transact-SQL)](assetId:///be7d8a59-3c00-4f1b-b4b0-3dcd5572e002)   
 [sys.server_sql_modules (Transact-SQL)](assetId:///9ef9a8b9-c470-4a61-b0c4-ee24ad871d63)   
 [sys.server_assembly_modules (Transact-SQL)](assetId:///af799e38-2d16-49b2-bcf5-6f9199af899e)