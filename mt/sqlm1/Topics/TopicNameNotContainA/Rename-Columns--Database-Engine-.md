---
title: Rename Columns (Database Engine)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
---
# Rename Columns (Database Engine)
  You can rename a table column in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To rename columns, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 Renaming a column will not automatically rename references to that column. You must modify any objects that reference the renamed column manually. For example, if you rename a table column and that column is referenced in a trigger, you must modify the trigger to reflect the new column name. Use [sys.sql\_expression\_dependencies](../Topic/sys.sql_expression_dependencies%20\(Transact-SQL\).md) to list dependencies on the object before renaming it.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the object.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To rename a column using Object Explorer  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  In **Object Explorer**, right\-click the table in which you want to rename columns and choose **Rename**.  
  
3.  Type a new column name.  
  
#### To rename a column using Table Designer  
  
1.  In **Object Explorer**, right\-click the table to which you want to rename columns and choose **Design**.  
  
2.  Under **Column Name**, select the name you want to change and type a new one.  
  
3.  On the **File** menu, click **Save***table name*.  
  
> [!NOTE]  
>  You can also change the name of a column in the **Column Properties** tab. Select the column whose name you want to change and type a new value for **Name**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To rename a column**  
  
#### To rename a column  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  The following example renames the column `TerritoryID` in the table `Sales.SalesTerritory` to `TerrID`. Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 For more information, see [sp_rename &#40;Transact-SQL&#41;](../Topic/sp_rename%20\(Transact-SQL\).md).  
  
  