---
title: "Get Information About DML Triggers"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-dml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37574aac-181d-4aca-a2cc-8abff64237dc
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Get Information About DML Triggers
This topic describes how to get information about DML triggers in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. This information can include the types of triggers on a table, the name of a trigger, its owner and the date it was created or modified. If the trigger was not encrypted when it was created, you obtain the definition of the trigger. You can use the definition to help you understand how a trigger affects the table up on which it is defined. Also, you can find out the objects that a specific trigger uses. With this information, you can identify the objects that affect the trigger if they are changed or deleted in the database.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To get information about DML triggers, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 **sys.sql.modules**, **sys.object**, **sys.triggers**, **sys.events**, **sys.trigger_events**  
 [!INCLUDE[ssCatViewPerm](../../Topics/TopicNameNotContainA/tokens/ssCatViewPerm_md.md)] For more information, see [Metadata Visibility Configuration](../../Topics/TopicNameNotContainA/Metadata-Visibility-Configuration.md).  
  
 OBJECT_DEFINITION, OBJECTPROPERTY, **sp_helptext**  
 Requires membership in the **public** role. The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION. These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.  
  
 **sys.sql_expression_dependencies**  
 Requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database. By default, SELECT permission is granted only to members of the **db_owner** fixed database role. When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view the definition of a DML trigger  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger for which you want to view the definition.  
  
3.  Expand **Triggers**, right-click the trigger you want, and then click **Modify**. The definition of the DML trigger appears in the query window.  
  
#### To view the dependencies of a DML trigger  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger and its dependencies that you want to view.  
  
3.  Expand **Triggers**, right-click the trigger you want, and then click **View Dependencies**.  
  
4.  In the **Object Dependencies** window, to view the objects that depend on the DML trigger, select **Objects that depend on <DML trigger name\>**. The objects appear in the **Dependencies** area.  
  
     To view the objects on which the DML depends, select **Objects on which <DML trigger name\> depends**. The objects appear in the **Dependencies** area. Expand each node to see all the objects.  
  
5.  To obtain information about an object that appears in the **Dependencies** area, click the object. In the **Selected object** field, information is provided in the **Name**, **Type**, and **Dependency type** boxes.  
  
6.  To close the **Object Dependencies** window, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To view the definition of a DML trigger  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste one of the following examples into the query window and click **Execute**. Each example shows how you can view the definition of the `iuPerson` trigger.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT definition   
FROM sys.sql_modules  
WHERE object_id = OBJECT_ID(N'Person.iuPerson');   
GO  
```  
  
```tsql  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.iuPerson')) AS ObjectDefinition;   
GO  
  
```  
  
```tsql  
USE AdventureWorks2012;   
GO  
EXEC sp_helptext 'Person.iuPerson'  
GO  
  
```  
  
#### To view the dependencies of a DML trigger  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste one of the following examples into the query window and click **Execute**. Each example shows how you can view the dependencies of `iuPerson` trigger.  
  
```  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc, referenced_class_desc,   
    referenced_server_name, referenced_database_name, referenced_schema_name,   
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,   
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referencing_id = OBJECT_ID(N'Person.iuPerson');   
GO  
  
```  
  
#### To view information about DML triggers in the database  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste one of the following examples into the query window and click **Execute**. Each example shows how you can view information about DML triggers (`TR`) in the database.  
  
```  
USE AdventureWorks2012;   
GO  
SELECT  name, parent_id, create_date, modify_date, is_instead_of_trigger  
FROM sys.triggers  
WHERE type = 'TR';   
GO  
  
```  
  
```tsql  
USE AdventureWorks2012;   
GO  
SELECT  name, object_id, schema_id, parent_object_id, type_desc, create_date, modify_date, is_published  
FROM sys.objects  
WHERE type = 'TR';   
GO  
  
```  
  
```tsql  
USE AdventureWorks2012;   
GO  
SELECT OBJECTPROPERTY(OBJECT_ID(N'Person.iuPerson'), 'ExecIsInsteadOfTrigger');   
GO  
  
```  
  
#### To view information about events that fire a DML trigger  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste one of the following examples into the query window and click **Execute**. Each example shows how you can view the events that fire the `iuPerson` trigger.  
  
```tsql  
USE AdventureWorks2012;   
GO  
SELECT object_id, type, type_desc, is_trigger_event, event_group_type, event_group_type_desc   
FROM sys.events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
```tsql  
USE AdventureWorks2012;   
GO   
SELECT object_id, type,is_first, is_last  
FROM sys.trigger_events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
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
 [OBJECTPROPERTY](assetId:///27569888-f8b5-4cec-a79f-6ea6d692b4ae)   
 [OBJECT_DEFINITION (Transact-SQL)](assetId:///2ac837c7-eca9-4d29-b06e-72e30450c68d)