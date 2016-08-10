---
title: "Manage Trigger Security"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-dml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e94720a8-a3a2-4364-b0a3-bbe86e3ce4d5
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Manage Trigger Security
By default, both DML and DDL triggers execute under the context of the user that calls the trigger. The caller of a trigger is the user that executes the statement that causes the trigger to run. For example, if user **Mary** executes a DELETE statement that causes DML trigger **DML_trigMary** to run, the code inside **DML_trigMary** executes in the context of the user privileges for **Mary**. This default behavior can be exploited by users who want to introduce malicious code in the database or server instance. For example, the following DDL trigger is created by user `JohnDoe`:  
  
 `CREATE TRIGGER DDL_trigJohnDoe`  
  
 `ON DATABASE`  
  
 `FOR ALTER_TABLE`  
  
 `AS`  
  
 `GRANT CONTROL SERVER TO JohnDoe ;`  
  
 `GO`  
  
 What this trigger means is that as soon as a user that has permission to execute a `GRANT CONTROL SERVER` statement, such as a member of the **sysadmin** fixed server role, executes an `ALTER TABLE` statement, `JohnDoe` is granted `CONTROL SERVER` permission. In other words, although `JohnDoe` cannot grant `CONTROL SERVER` permission to himself, he enabled the trigger code that grants him this permission to execute under escalated privileges. Both DML and DDL triggers are open to this kind of security threat.  
  
## Trigger Security Best Practices  
 You can take the following measures to prevent trigger code from executing under escalated privileges:  
  
-   Be aware of the DML and DDL triggers that exist in the database and on the server instance by querying the [sys.triggers](assetId:///cefa4fc4-b8b9-4cd7-b124-eed5283acbfc) and [sys.server_triggers](assetId:///25926ff4-9271-45bf-bc32-d5d3344bd47a) catalog views. The following query returns all DML and database-level DDL triggers in the current database, and all server-level DDL triggers on the server instance:  
  
    ```  
    SELECT type, name, parent_class_desc FROM sys.triggers  
    UNION  
    SELECT type, name, parent_class_desc FROM sys.server_triggers ;  
    ```  
  
-   Use [DISABLE TRIGGER](assetId:///e6529f06-e442-437e-a7bf-41790bc092c5) to disable triggers that can harm the integrity of the database or server if the triggers execute under escalated privileges. The following statement disables all database-level DDL triggers in the current database:  
  
    ```  
    DISABLE TRIGGER ALL ON DATABASE  
    ```  
  
     This statement disables all server-level DDL triggers on the server instance:  
  
    ```  
    DISABLE TRIGGER ALL ON ALL SERVER  
    ```  
  
     This statement disables all DML triggers in the current database:  
  
    ```  
    DECLARE @schema_name sysname, @trigger_name sysname, @object_name sysname ;  
    DECLARE @sql nvarchar(max) ;  
    DECLARE trig_cur CURSOR FORWARD_ONLY READ_ONLY FOR  
        SELECT SCHEMA_NAME(schema_id) AS schema_name,  
            name AS trigger_name,  
            OBJECT_NAME(parent_object_id) as object_name  
        FROM sys.objects WHERE type in ('TR', 'TA') ;  
  
    OPEN trig_cur ;  
    FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        SELECT @sql = 'DISABLE TRIGGER ' + QUOTENAME(@schema_name) + '.'  
            + QUOTENAME(@trigger_name) +  
            ' ON ' + QUOTENAME(@schema_name) + '.'   
            + QUOTENAME(@object_name) + ' ; ' ;  
        EXEC (@sql) ;  
        FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
    END  
    GO  
  
    -- Verify triggers are disabled. Should return an empty result set.  
    SELECT * FROM sys.triggers WHERE is_disabled = 0 ;  
    GO  
  
    CLOSE trig_cur ;  
    DEALLOCATE trig_cur;  
    ```  
  
## See Also  
 [Designing DDL Triggers](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7)   
 [DML Triggers](../../Topics/TopicNameNotContainA/DML-Triggers.md)   
 [DDL Triggers](../../Topics/TopicNameNotContainA/DDL-Triggers.md)