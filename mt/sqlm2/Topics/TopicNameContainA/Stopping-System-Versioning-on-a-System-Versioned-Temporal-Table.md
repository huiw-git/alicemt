---
title: Stopping System-Versioning on a System-Versioned Temporal Table
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dddd707e-bfb1-44ff-937b-a84c5e5d1a94
---
# Stopping System-Versioning on a System-Versioned Temporal Table
  You may want to stop versioning on your temporal table either temporarily or permanently.   
You can do that by setting **SYSTEM\_VERSIONING** clause to **OFF**.  
  
## Setting SYSTEM\_VERSIONING \= OFF  
 Stop system\-versioning if you want to perform specific maintenance operations on temporal table or if you don’t need a versioned table anymore. As a result of this operation you will get two independent tables:  
  
-   Current table with period definition  
  
-   History table as a regular table  
  
### Important remarks  
  
-   No data loss happens when you set  **SYSTEM\_VERSIONING \= OFF** or drop the **SYSTEM\_TIME** period.  
  
-   When you set **SYSTEM\_VERSIONING \= OFF** and do not remove drop the **SYSTEM\_TIME** period, the system will continue to update the period columns for every insert and update operation. Deletes on current table will be permanent.  
  
-   Drop the **SYSTEM\_TIME** period to remove the period columns completely.  
  
-   When you set **SYSTEM\_VERSIONING \= OFF**, all users that have sufficient permissions will be able to modify schema and content of history table or even to permanently delete the history table.  
  
-   Prior to [!INCLUDE[ssCurrentLong](../../Token\Other/ssCurrentLong_md.md)], changing the schema of a temporal table required you to set **SYSTEM\_VERSIONING \= OFF**. However, beginning with  [!INCLUDE[ssCurrentLong](../../Token\Other/ssCurrentLong_md.md)], you can now add, drop or alter temporal table columns without changing system\-versioning state.  
  
### Permanently remove SYSTEM\_VERSIONING  
 This example permanently removes SYSTEM\_VERSIONING and removes the period columns completely. Removing the period columns is optional.  
  
```  
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
/*Optionally, DROP PERIOD if you want to revert temporal table to a non-temporal*/   
ALTER TABLE dbo.Department   
DROP PERIOD FOR SYSTEM_TIME;  
  
```  
  
### Temporarily remove SYSTEM\_VERSIONING  
 This is the list of operations that requires system\-versioning to be set to **OFF**:  
  
-   Removing unnecessary data from history \(**DELETE** or **TRUNCATE**\)  
  
-   Removing data from current table without versioning \(**DELETE**, **TRUNCATE**\)  
  
-   Partition **SWITCH OUT** from current table  
  
-   Partition **SWITCH IN** into history table  
  
 This example temporarily stops SYSTEM\_VERSIONING to allow you to perform specific maintenance operations. If you stop versioning temporarily as a prerequisite for table maintenance, we strongly recommend doing this inside a transaction to keep data consistency.  
  
```  
BEGIN TRAN   
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
TRUNCATE TABLE [History].[DepartmentHistory]   
WITH (PARTITIONS (1,2))   
ALTER TABLE dbo.Department SET    
(   
SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.DepartmentHistory)   
);   
COMMIT ;  
  
```  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Stopping%20System-Versioning%20on%20a%20System-Version%20Temporal%20Table%20page)  
  
## See Also  
 [Temporal Tables](../../Topics\TopicNameNotContainA/Temporal-Tables.md)   
 [Getting Started with System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Getting-Started-with-System-Versioned-Temporal-Tables.md)   
 [Manage Retention of Historical Data in System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Manage-Retention-of-Historical-Data-in-System-Versioned-Temporal-Tables.md)   
 [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)   
 [Creating a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Creating-a-System-Versioned-Temporal-Table.md)   
 [Modifying Data in a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Modifying-Data-in-a-System-Versioned-Temporal-Table.md)   
 [Querying Data in a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Querying-Data-in-a-System-Versioned-Temporal-Table.md)   
 [Changing the Schema of a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Changing-the-Schema-of-a-System-Versioned-Temporal-Table.md)  
  
  