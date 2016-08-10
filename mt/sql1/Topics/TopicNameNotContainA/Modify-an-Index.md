---
title: "Modify an Index"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-indexes
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Modify an Index
This topic describes how to modify an index in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
> [!IMPORTANT]  
>  Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be modified by using this method. Instead, the constraint must be modified.  
  
 **In This Topic**  
  
-   **To modify an index, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To modify an index  
  
1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the table belongs, and then expand **Tables**.  
  
3.  Expand the table in which the index belongs and then expand **Indexes**.  
  
4.  Right-click the index that you want to modify and then click **Properties**.  
  
5.  In the **Index Properties** dialog box, make the desired changes. For example, you can add or remove a column from the index key, or change the setting of an index option.  
  
#### To modify index columns  
  
1.  To add, remove, or change the position of an index column, select the **General** page from the **Index Properties** dialog box.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To modify an index  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example drops and re-creates an existing index on the `ProductID` column of the `Production.WorkOrder` table by using the `DROP_EXISTING` option. The options `FILLFACTOR` and `PAD_INDEX` are also set.  
  
     [!CODE [IndexDDL#CreateIndex4](../CodeSnippet/SQL15/tsql/indexddl#createindex4)]  
  
     The following example uses ALTER INDEX to set several options on the index `AK_SalesOrderHeader_SalesOrderNumber`.  
  
     [!CODE [IndexDDL#AlterIndex4](../CodeSnippet/SQL15/tsql/indexddl#alterindex4)]  
  
#### To modify index columns  
  
1.  To add, remove, or change the position of an index column, you must drop and recreate the index.  
  
## See Also  
 [CREATE INDEX (Transact-SQL)](assetId:///d2297805-412b-47b5-aeeb-53388349a5b9)   
 [ALTER INDEX (Transact-SQL)](assetId:///b796c829-ef3a-405c-a784-48286d4fb2b9)   
 [INDEXPROPERTY (Transact-SQL)](assetId:///998d5788-4871-44a8-8125-0d9390868b84)   
 [sys.indexes (Transact-SQL)](assetId:///066bd9ac-6554-4297-88fe-d740de1f94a8)   
 [sys.index_columns (Transact-SQL)](assetId:///211471aa-558a-475c-9b94-5913c143ed12)   
 [Set Index Options](../../Topics/TopicNameNotContainA/Set-Index-Options.md)   
 [Rename Indexes](../../Topics/TopicNameNotContainA/Rename-Indexes.md)