---
title: Working with Memory-Optimized System-Versioned Temporal Tables
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 691d4f80-6754-43f5-8b43-d4facf08f6fc
---
# Working with Memory-Optimized System-Versioned Temporal Tables
  This topic discusses how working with a memory\-optimized system\-versioned temporal table is different from working with a disk\-based system\-versioned temporal table.  
  
> [!NOTE]  
>  Using Temporal with memory optimized tables only applies to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and does not apply to [!INCLUDE[sqldbesa](../../Token\Other/sqldbesa_md.md)].  
  
## Discovering Metadata  
 To discover metadata about a memory\-optimized system\-versioned temporal table, you need to combine information from [sys.tables &#40;Transact-SQL&#41;](../Topic/sys.tables%20\(Transact-SQL\).md) and [sys.internal_tables &#40;Transact-SQL&#41;](../Topic/sys.internal_tables%20\(Transact-SQL\).md). A system\-versioned temporal table is presented as parent\_object\_id of the internal in\-memory history table  
  
 This example shows how to query and join these tables.  
  
```  
SELECT SCHEMA_NAME (T1.schema_id) as TemporalTableSchema  
   , OBJECT_NAME(IT.parent_object_id) as TemporalTableName  
   , T1.object_id as TemporalTableObjectId  
   , IT.Name as InternalHistoryStagingName   
   , SCHEMA_NAME (T2.schema_id) as HistoryTableSchema  
   , OBJECT_NAME (T1.history_table_id) as HistoryTableName   
FROM sys.internal_tables IT    
JOIN sys.tables T1   
   ON IT.parent_object_id = T1.object_id   
JOIN sys.tables T2   
   ON T1.history_table_id = T2.object_id   
WHERE T1.is_memory_optimized  = 1 AND T1.temporal_type = 2  
  
```  
  
## Modifying Data  
 System\-versioned memory\-optimized temporal tables can be modified through natively compiled stored procedures, which enables you to convert non\-temporal memory\-optimized tables to system\-versioning and keep existing natively stored procedures.  
  
 This example how previously created table can be modified in natively compiled module.  
  
```  
CREATE PROCEDURE dbo.UpdateFXCurrencyPair  
   (   
       @ProviderID int  
     , @CurrencyID1 int  
     , @CurrencyID2 int  
     , @BidRate decimal(8,4)  
     , @AskRate decimal(8,4)   
   )   
WITH NATIVE_COMPILATION, SCHEMABINDING  
   , EXECUTE AS OWNER   
AS    
   BEGIN ATOMIC WITH   
   (TRANSACTION ISOLATION LEVEL = SNAPSHOT  , LANGUAGE = N'English')   
      UPDATE dbo.FXCurrencyPairs SET AskRate = @AskRate, BidRate  = @BidRate   
     WHERE ProviderID = @ProviderID AND CurrencyID1 = @CurrencyID1 AND CurrencyID2 = @CurrencyID2   
END   
GO ;  
  
```  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Working%20with%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page)  
  
## See Also  
 [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)   
 [Creating a Memory-Optimized System-Versioned Temporal Table](../../Topics\TopicNameContainA/Creating-a-Memory-Optimized-System-Versioned-Temporal-Table.md)   
 [Monitoring Memory-Optimized System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Monitoring-Memory-Optimized-System-Versioned-Temporal-Tables.md)   
 [Performance Considerations with Memory-Optimized System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Performance-Considerations-with-Memory-Optimized-System-Versioned-Temporal-Tables.md)   
 [Temporal Tables](../../Topics\TopicNameNotContainA/Temporal-Tables.md)   
 [Temporal Table System Consistency Checks](../../Topics\TopicNameNotContainA/Temporal-Table-System-Consistency-Checks.md)   
 [Manage Retention of Historical Data in System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Manage-Retention-of-Historical-Data-in-System-Versioned-Temporal-Tables.md)   
 [Temporal Table Metadata Views and Functions](../../Topics\TopicNameNotContainA/Temporal-Table-Metadata-Views-and-Functions.md)  
  
  