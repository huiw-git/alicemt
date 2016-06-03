---
title: Delete an Index
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-indexes
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
---
# Delete an Index
  This topic describes how to delete \(drop\) an index in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To delete an index, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be deleted by using this method. Instead, the constraint must be deleted. To remove the constraint and corresponding index, use [ALTER TABLE](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md) with the DROP CONSTRAINT clause in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. For more information, see [Delete Primary Keys](../../Topics\TopicNameNotContainA/Delete-Primary-Keys.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table or view. This permission is granted by default to the **sysadmin** fixed server role and the **db\_ddladmin** and **db\_owner** fixed database roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To delete an index by using Object Explorer  
  
1.  In Object Explorer, expand the database that contains the table on which you want to delete an index.  
  
2.  Expand the **Tables** folder.  
  
3.  Expand the table that contains the index you want to delete.  
  
4.  Expand the **Indexes** folder.  
  
5.  Right\-click the index you want to delete and select **Delete**.  
  
6.  In the **Delete Object** dialog box, verify that the correct index is in the **Object to be deleted** grid and click **OK**.  
  
#### To delete an index using Table Designer  
  
1.  In Object Explorer, expand the database that contains the table on which you want to delete an index.  
  
2.  Expand the **Tables** folder.  
  
3.  Right\-click the table that contains the index you want to delete and click Design.  
  
4.  On the **Table Designer** menu, click **Indexes\/Keys**.  
  
5.  In the **Indexes\/Keys** dialog box, select the index you want to delete.  
  
6.  Click **Delete**.  
  
7.  Click **Close**.  
  
8.  On the **File** menu, select **Save***table\_name*.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To delete an index  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 For more information, see [DROP INDEX &#40;Transact-SQL&#41;](../Topic/DROP%20INDEX%20\(Transact-SQL\).md).  
  
  