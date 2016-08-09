---
title: "Manage Change Tracking (SQL Server)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94a8d361-e897-4d6d-9a8f-1bb652e7a850
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Manage Change Tracking (SQL Server)
This topic describes how to manage change tracking. It also describes how to configure security and determine the effects on storage and performance when change tracking is used.  
  
## Managing Change Tracking  
 The following sections list catalog views, permissions, and settings that are relevant for managing change tracking.  
  
### Catalog Views  
 To determine which tables and databases have change tracking enabled, you can use the following catalog views:  
  
-   [sys.change_tracking_databases](assetId:///bb233baa-2991-4904-a0eb-3772b81121a4)  
  
-   [sys.change_tracking_tables](assetId:///97ec69b6-0d49-4d98-82f0-d3e77ba1ad2b)  
  
 Also, the [sys.internal_tables](assetId:///a5821c70-f150-4676-8476-3a31f7403dca) catalog view lists the internal tables that are created when change tracking is enabled for a user table.  
  
### Security  
 To access change tracking information by using the [change tracking functions](assetId:///04eb53c4-8b69-414e-9696-185d227fea35), the principal must have the following permissions:  
  
-   SELECT permission on at least the primary key columns on the change-tracked table to the table that is being queried.  
  
-   VIEW CHANGE TRACKING permission on the table for which changes are being obtained. The VIEW CHANGE TRACKING permission is required for the following reasons:  
  
    -   Change tracking records include information about rows that have been deleted, specifically the primary key values of the rows that have been deleted. A principal could have been granted SELECT permission for a change tracked table after some sensitive data had been deleted. In this case, you would not want that principal to be able to access that deleted information by using change tracking.  
  
    -   Change tracking information can store information about which columns have been changed by update operations. A principal could be denied permission to a column that contains sensitive information. However, because change tracking information is available, a principal can determine that a column value has been updated, but the principal cannot determine the value of the column.  
  
## Understanding Change Tracking Overhead  
 When change tracking is enabled for a table, some administration operations are affected. The following table lists the operations and the effects you should consider.  
  
|Operation|When change tracking is enabled|  
|---------------|-------------------------------------|  
|DROP TABLE|All change tracking information for the dropped table is removed.|  
|ALTER TABLE DROP CONSTRAINT|An attempt to drop the PRIMARY KEY constraint will fail. Change tracking must be disabled before a PRIMARY KEY constraint can be dropped.|  
|ALTER TABLE DROP COLUMN|If a column that is being dropped is part of the primary key, dropping the column is not allowed, regardless of change tracking.<br /><br /> If the column that is being dropped is not part of the primary key, dropping the column succeeds. However, the effect on any application that is synchronizing this data should be understood first. If column change tracking is enabled for the table, the dropped column might still be returned as part of the change tracking information. It is the responsibility of the application to handle the dropped column.|  
|ALTER TABLE ADD COLUMN|If a new column is added to the change tracked table, the addition of the column is not tracked. Only the updates and changes that are made to the new column are tracked.|  
|ALTER TABLE ALTER COLUMN|Data type changes of a non-primary key columns are not tracked.|  
|ALTER TABLE SWITCH|Switching a partition fails if one or both of the tables has change tracking enabled.|  
|DROP INDEX, or ALTER INDEX DISABLE|The index that enforces the primary key cannot be dropped or disabled.|  
|TRUNCATE TABLE|Truncating a table can be performed on a table that has change tracking enabled. However, the rows that are deleted by the operation are not tracked, and the minimum valid version is updated. When an application checks its version, the check indicates that the version is too old and a reinitialization is required. This is the same as change tracking being disabled, and then reenabled for the table.|  
  
 Using change tracking does add some overhead to DML operations because of the change tracking information that is being stored as part of the operation.  
  
### Effects on DML  
 Change tracking has been optimized to minimize the performance overhead on DML operations. The incremental performance overhead that is associated with using change tracking on a table is similar to the overhead incurred when an index is created for a table and needs to be maintained.  
  
 For each row that is changed by a DML operation, a row is added to the internal change tracking table. The effect of this relative to the DML operation depends on various factors, such as the following:  
  
-   The number of primary key columns  
  
-   The amount of data that is being changed in the user table row  
  
-   The number of operations that are being performed in a transaction  
  
 Snapshot isolation, if used, also has an effect on performance for all DML operations, whether change tracking is enabled or not.  
  
### Effects on Storage  
 Change tracking data is stored in the following types of internal tables:  
  
-   Internal change table  
  
     There is one internal change table for each user table that has change tracking enabled.  
  
-   Internal transaction table  
  
     There is one internal transaction table for the database.  
  
 These internal tables affect storage requirements in the following ways:  
  
-   For each change to each row in the user table, a row is added to the internal change table. This row has a small fixed overhead plus a variable overhead equal to the size of the primary key columns. The row can contain optional context information set by an application. And, if column tracking is enabled, each changed column requires 4 bytes in the tracking table.  
  
-   For each committed transaction, a row is added to an internal transaction table.  
  
 As with other internal tables, you can determine the space used for the change tracking tables by using the [sp_spaceused](assetId:///c6253b48-29f5-4371-bfcd-3ef404060621) stored procedure. The names of the internal tables can be obtained by using the [sys.internal_tables](assetId:///a5821c70-f150-4676-8476-3a31f7403dca) catalog view, as shown in the following example.  
  
```tsql  
sp_spaceused 'sys.change_tracking_309576141'  
sp_spaceused 'sys.syscommittab'  
```  
  
## See Also  
 [Track Data Changes (SQL Server)](../../Topics/TopicNameNotContainA/Track-Data-Changes--SQL-Server-.md)   
 [ALTER TABLE](assetId:///f1745145-182d-4301-a334-18f799d361d1)   
 [Database Properties (ChangeTracking Page)](../../Topics/TopicNameNotContainA/Database-Properties--ChangeTracking-Page-.md)   
 [ALTER DATABASE](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc)   
 [sys.change_tracking_databases](assetId:///bb233baa-2991-4904-a0eb-3772b81121a4)   
 [sys.change_tracking_tables](assetId:///97ec69b6-0d49-4d98-82f0-d3e77ba1ad2b)   
 [Track Data Changes (SQL Server)](../../Topics/TopicNameNotContainA/Track-Data-Changes--SQL-Server-.md)   
 [About Change Tracking (SQL Server)](../../Topics/TopicNameNotContainA/About-Change-Tracking--SQL-Server-.md)   
 [Work with Change Data (SQL Server)](../../Topics/TopicNameNotContainA/Work-with-Change-Data--SQL-Server-.md)