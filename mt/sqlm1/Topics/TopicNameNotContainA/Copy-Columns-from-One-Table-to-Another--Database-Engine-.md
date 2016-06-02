---
title: Copy Columns from One Table to Another (Database Engine)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
---
# Copy Columns from One Table to Another (Database Engine)
  This topic describes how to copy columns from one table to another, copying either just the column definition, or the definition and data in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To coy columns, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 When you copy a column that has an alias data type from one database to another, the alias data type may not be available in the destination database. In such a case, the column will be assigned the nearest matching base data type available in that database.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To copy column definitions from one table to another  
  
1.  Open the table with columns you want to copy and the one you want to copy into by right\-clicking the tables, and then clicking **Design**.  
  
2.  Click the tab for the table with the columns you want to copy and select those columns.  
  
3.  From the **Edit** menu, click **Copy**.  
  
4.  Click the tab for the table into which you want to copy the columns.  
  
5.  Select the column you want to follow the inserted columns and, from the **Edit** menu, click **Paste**.  
  
#### To copy data from one table to another  
  
1.  Follow the directions for copying column definitions above.  
  
    > [!NOTE]  
    >  Before you begin to copy data from one table to another, make sure that the data types in the destination columns are compatible with the data types of the source columns  
  
2.  In Object Explorer, right\-click the **Views** node, and then click **New View**.  
  
3.  From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.  
  
4.  In the **Choose Target Table for Insert Results** dialog box, select the table into which you want to copy the data, and then click **OK**.  
  
     If you are copying rows within a table, you can add the source table as a destination table.  
  
    > [!NOTE]  
    >  **Query Designer** cannot determine in advance which tables and views you can update. Therefore, the list of tables in the **Choose Target Table for Insert Results** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.  
  
5.  Right\-click in the body of the diagram pane and, from the shortcut menu, click **Add Table to Diagram**.  
  
6.  In the **Add Table** dialog box, select each table from which you want to copy data, click **Add**, and then click **Close**.  
  
     The tables, in an abbreviated form, appear in the diagram pane.  
  
7.  In the abbreviated tables, check the boxes for any columns from which you want to copy data.  
  
8.  In the criteria pane, in the **Append** column, for each target column choose a column from which you want to copy data.  
  
9. Specify the rows to copy by entering search conditions in the criteria pane. For details, see [Specify Search Conditions &#40;Visual Database Tools&#41;](../Topic/Specify%20Search%20Conditions%20\(Visual%20Database%20Tools\).md).  
  
     If you do not specify a search condition, all rows from the source table will be copied to the destination table.  
  
10. If you want to copy summary information, specify **Group By** options. For details, see [Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;](../Topic/Summarize%20or%20Aggregate%20Values%20for%20All%20Rows%20in%20a%20Table%20\(Visual%20Database%20Tools\).md).  
  
11. Click the **Execute SQL button** to run the query.  
  
     When you execute an insert results query, no results are reported in the [Results Pane](../Topic/Results%20Pane%20\(Visual%20Database%20Tools\).md). Instead, a message appears indicating how many rows were copied.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To copy column definitions from one table to another  
  
1.  You cannot copy individual columns from one table to another existing table by using Transact\-SQL statements. However, you can create a new table in the default filegroup and inserts the resulting rows from the query into it by using SELECT INTO. For more information, see [INTO Clause &#40;Transact-SQL&#41;](../Topic/INTO%20Clause%20\(Transact-SQL\).md).  
  
#### To copy data from one table to another  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  