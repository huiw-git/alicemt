---
title: Perform Index Operations Online
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-indexes
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
---
# Perform Index Operations Online
  This topic describes how to create, rebuild, or drop indexes online in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The ONLINE option allows concurrent user access to the underlying table or clustered index data and any associated nonclustered indexes during these index operations. For example, while a clustered index is being rebuilt by one user, that user and others can continue to update and query the underlying data. When you perform data definition language \(DDL\) operations offline, such as building or rebuilding a clustered index; these operations hold exclusive locks on the underlying data and associated indexes. This prevents modifications and queries to the underlying data until the index operation is complete.  
  
> [!NOTE]  
>  Online index operations are not available in every [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition. For more information, see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To rebuild an index online, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   We recommend performing online index operations for business environments that operate 24 hours a day, seven days a week, in which the need for concurrent user activity during index operations is vital.  
  
-   The ONLINE option is available in the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements.  
  
    -   [CREATE INDEX](../Topic/CREATE%20INDEX%20\(Transact-SQL\).md)  
  
    -   [ALTER INDEX](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md)  
  
    -   [DROP INDEX](../Topic/DROP%20INDEX%20\(Transact-SQL\).md)  
  
    -   [ALTER TABLE](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md) \(To add or drop UNIQUE or PRIMARY KEY constraints with CLUSTERED index option\)  
  
-   For more limitations and restrictions concerning creating, rebuilding, or dropping indexes online, see [Guidelines for Online Index Operations](../../Topics\TopicNameNotContainA/Guidelines-for-Online-Index-Operations.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table or view.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To rebuild an index online  
  
1.  In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rebuild an index online.  
  
2.  Expand the **Tables** folder.  
  
3.  Click the plus sign to expand the table on which you want to rebuild an index online.  
  
4.  Expand the **Indexes** folder.  
  
5.  Right\-click the index that you want to rebuild online and select **Properties**.  
  
6.  Under **Select a page**, select **Options**.  
  
7.  Select **Allow online DML processing**, and then select **True** from the list.  
  
8.  Click **OK**.  
  
9. Right\-click the index that you want to rebuild online and select **Rebuild**.  
  
10. In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To create, rebuild, or drop an index online  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The example rebuilds an existing online  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     The following example deletes a clustered index online and moves the resulting table \(heap\) to the filegroup `NewGroup` by using the `MOVE TO` clause. The `sys.indexes`, `sys.tables`, and `sys.filegroups` catalog views are queried to verify the index and table placement in the filegroups before and after the move.  
  
     [!CODE [IndexDDL#DropIndex4](../CodeSnippet/SQL15/tsql/indexddl#dropindex4)]  
  
 For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md).  
  
  