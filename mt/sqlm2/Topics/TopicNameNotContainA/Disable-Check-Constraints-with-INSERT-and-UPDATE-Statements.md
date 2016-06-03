---
title: Disable Check Constraints with INSERT and UPDATE Statements
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
---
# Disable Check Constraints with INSERT and UPDATE Statements
  You can disable a check constraint for INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. After you disable the check constraints, future inserts or updates to the column will not be validated against the constraint conditions. Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To disable a check constraint for INSERT and UPDATE statements, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To disable a check constraint for INSERT and UPDATE statements  
  
1.  In **Object Explorer**, expand the table with the constraint and then expand the **Constraints** folder.  
  
2.  Right\-click the constraint and select **Modify**.  
  
3.  In the grid under **Table Designer**, click **Enforce For INSERTs And UPDATEs** and select **No** from the drop\-down menu.  
  
4.  Click **Close**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To disable a check constraint for INSERT and UPDATE statements  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following examples into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md).  
  
###  <a name="TsqlExample"></a>  