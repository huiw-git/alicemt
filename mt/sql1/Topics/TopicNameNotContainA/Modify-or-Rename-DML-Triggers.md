---
title: "Modify or Rename DML Triggers"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-dml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7317eec-c0e9-479e-a4a7-83b6b6c58d59
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Modify or Rename DML Triggers
This topic describes how to modify or rename a DML trigger in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To modify or rename a DML trigger, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   When you rename a trigger, the trigger must be in the current database, and the new name must follow the rules for [identifiers](../../Topics/TopicNameNotContainA/Database-Identifiers.md).  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   We recommend you do not use the [sp_rename](assetId:///bc3548f0-143f-404e-a2e9-0a15960fc8ed) stored procedure to rename a trigger. Changing any part of an object name can break scripts and stored procedures. Renaming a trigger does not change the name of the corresponding object name in the definition column of the [sys.sql_modules](assetId:///23d3ccd2-f356-4d89-a2cd-bee381243f99) catalog view. We recommend that you drop and and re-create the trigger instead.  
  
-   If you change the name of an object referenced by a DML trigger, you must modify the trigger so that its text reflects the new name. Therefore, before you rename an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.  
  
-   A DML trigger can also be modified to encrypt its definition.  
  
-   To view the dependencies of a trigger, you can use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or the following function and catalog views:  
  
    -   [sys.sql_expression_dependencies (Transact-SQL)](assetId:///78a218e4-bf99-4a6a-acbf-ff82425a5946)  
  
    -   [sys.dm_sql_referenced_entities](assetId:///077111cb-b860-4d61-916f-bac5d532912f)  
  
    -   [sys.dm_sql_referencing_entities](assetId:///c16f8f0a-483f-4feb-842e-da90426045ae)  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 To alter a DML trigger requires ALTER permission on the table or view on which the trigger is defined.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To modify a DML trigger  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to modify.  
  
3.  Expand **Triggers**, right-click the trigger to modify, and then click **Modify**.  
  
4.  Modify the trigger, and then click **Execute**.  
  
#### To rename a DML trigger  
  
1.  [Delete the trigger](../../Topics/TopicNameNotContainA/Delete-or-Disable-DML-Triggers.md) that you want to rename.  
  
2.  [Re-create the trigger](../../Topics/TopicNameNotContainA/Create-DML-Triggers.md), specifying the new name.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To modify a trigger using ALTER TRIGGER  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following examples into the query. Execute the first example to create a DML trigger that prints a user-defined message to the client when a user tries to add or change data in the `SalesPersonQuotaHistory` table. Execute the [ALTER TRIGGER](assetId:///2a99c7c1-ac2f-4637-aa7c-3d1bf514e500) statement to modify the trigger to fire only on `INSERT` activities. This trigger is helpful because it reminds the user that updates or inserts rows into this table to also notify the `Compensation` department.  
  
```tsql  
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
USE AdventureWorks2012;  
GO  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
#### To rename a trigger using DROP TRIGGER and ALTER TRIGGER  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example use the [DROP TRIGGER](assetId:///092d0d71-9f1e-4e38-a1c4-2487adfa5b4e) and [ALTER TRIGGER](assetId:///2a99c7c1-ac2f-4637-aa7c-3d1bf514e500) statements to rename the `Sales.bonus_reminder` trigger to `Sales.bonus_reminder_2`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder_2  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
## See Also  
 [CREATE TRIGGER (Transact-SQL)](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7)   
 [DROP TRIGGER (Transact-SQL)](assetId:///092d0d71-9f1e-4e38-a1c4-2487adfa5b4e)   
 [ENABLE TRIGGER (Transact-SQL)](assetId:///6e21f0ad-68d0-432f-9c7c-a119dd2d3fc9)   
 [DISABLE TRIGGER (Transact-SQL)](assetId:///e6529f06-e442-437e-a7bf-41790bc092c5)   
 [eventdata (Transact-SQL)](assetId:///03a80e63-6f37-4b49-bf13-dc35cfe46c44)   
 [sp_rename (Transact-SQL)](assetId:///bc3548f0-143f-404e-a2e9-0a15960fc8ed)   
 [ALTER TRIGGER (Transact-SQL)](assetId:///2a99c7c1-ac2f-4637-aa7c-3d1bf514e500)   
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