---
title: Modify Columns (Database Engine)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
---
# Modify Columns (Database Engine)
  You can modify the data type of a column in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
> [!WARNING]  
>  Modifying the data type of a column that already contains data can result in the permanent loss of data when the existing data is converted to the new type. In addition, code and applications that depend on the modified column may fail. These include queries, views, stored procedures, user\-defined functions, and client applications. Note that these failures will cascade. For example, a stored procedure that calls a user\-defined function that depends on the modified column may fail. Carefully consider any changes you want to make to a column before making it.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To modify the data type of a column, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To modify the data type of a column  
  
1.  In **Object Explorer**, right\-click the table with columns for which you want to change the scale and click **Design**.  
  
2.  Select the column for which you want to modify the data type.  
  
3.  In the **Column Properties** tab, click the grid cell for the **Data Type** property and choose a new data type from the drop\-down list.  
  
4.  On the **File** menu, click **Save***table name*.  
  
> [!NOTE]  
>  When you modify the data type of a column, Table Designer applies the default length of the data type you selected, even if you have already specified another. Always set the data type length for to the desired value after specifying the data type.  
  
> [!WARNING]  
>  If you attempt to modify the data type of a column that relates to other tables, Table Designer asks you to confirm that the change should be made to the columns in the other tables as well.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To modify the data type of a column  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md)  
  
  