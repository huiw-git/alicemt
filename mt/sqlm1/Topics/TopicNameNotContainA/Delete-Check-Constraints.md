---
title: Delete Check Constraints
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
---
# Delete Check Constraints
  You can delete a check constraint in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. Deleting check constraints removes the limitations on data values that are accepted in the column or columns included in the constraint expression.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To delete a check constraint, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To delete a check constraint  
  
1.  In **Object Explorer**, expand the table with the check constraint.  
  
2.  Expand  **Constraints**.  
  
3.  Right\-click the constraint and click **Delete**.  
  
4.  In the **Delete Object** dialog box, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To delete a check constraint  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md).  
  
  