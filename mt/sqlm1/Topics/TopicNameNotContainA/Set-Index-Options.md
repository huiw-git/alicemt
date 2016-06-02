---
title: Set Index Options
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-indexes
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
---
# Set Index Options
  This topic describes how to modify the properties of an index in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To modify the properties of an index, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The following options are immediately applied to the index by using the SET clause in the ALTER INDEX statement: ALLOW\_PAGE\_LOCKS, ALLOW\_ROW\_LOCKS, IGNORE\_DUP\_KEY, and STATISTICS\_NORECOMPUTE.  
  
-   The following options can be set when you rebuild an index by using either ALTER INDEX REBUILD or CREATE INDEX WITH DROP\_EXISTING: PAD\_INDEX, FILLFACTOR, SORT\_IN\_TEMPDB, IGNORE\_DUP\_KEY, STATISTICS\_NORECOMPUTE, ONLINE, ALLOW\_ROW\_LOCKS, ALLOW\_PAGE\_LOCKS, MAXDOP, and DROP\_EXISTING \(CREATE INDEX only\).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table or view.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To modify the properties of an index in Table Designer  
  
1.  In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index’s properties.  
  
2.  Click the plus sign to expand the **Tables** folder.  
  
3.  Right\-click the table on which you want to modify an index’s properties and select **Design**.  
  
4.  On the **Table Designer** menu, click **Indexes\/Keys**.  
  
5.  Select the index that you want to modify. Its properties will show up in the main grid.  
  
6.  Change the settings of any and all properties to customize the index.  
  
7.  Click **Close**.  
  
8.  On the **File** menu, select **Save***table\_name*.  
  
#### To modify the properties of an index in Object Explorer  
  
1.  In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index’s properties.  
  
2.  Click the plus sign to expand the **Tables** folder.  
  
3.  Click the plus sign to expand the table on which you want to modify an index’s properties.  
  
4.  Click the plus sign to expand the **Indexes** folder.  
  
5.  Right\-click the index of which you want to modify the properties and select **Properties**.  
  
6.  Under **Select a page**, select **Options**.  
  
7.  Change the settings of any and all properties to customize the index.  
  
8.  To add, remove, or change the position of an index column, select the **General** page from the **Index Properties \-** *index\_name* dialog box. For more information, see [Index Properties F1 Help](../../Topics\TopicNameNotContainA/Index-Properties-F1-Help.md)  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To see the properties of all the indexes in a table  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### To set the properties of an index  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following examples into the query window and click **Execute**.  
  
     [!CODE [IndexDDL#AlterIndex4](../CodeSnippet/SQL15/tsql/indexddl#alterindex4)]  
  
     [!CODE [IndexDDL#AlterIndex2](../CodeSnippet/SQL15/tsql/indexddl#alterindex2)]  
  
 For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md).  
  
  