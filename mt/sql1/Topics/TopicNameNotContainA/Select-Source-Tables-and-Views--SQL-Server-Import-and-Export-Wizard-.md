---
title: "Select Source Tables and Views (SQL Server Import and Export Wizard)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
caps.latest.revision: 63
caps.handback.revision: 0
manager: jhubbard
---
# Select Source Tables and Views (SQL Server Import and Export Wizard)
After you specify whether you want to copy an entire table or only certain rows, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard shows **Select Source Tables and Views**. On this page, you select the existing tables and views to copy or review the query that you provided. Optionally you choose columns to copy and preview sample data.  
  
 When you select **Copy data from one or more tables or views** on the **Select Table Copy or Query** page, you can copy from one table or view to one destination table, or from multiple tables or views to multiple destination tables.  
  
 You don't have to copy all the columns in a table when you select the Table Copy option. On the **Select Source Tables and Views** page, click **Edit Mappings** to display the **Column Mappings** dialog box for the selected table. Select **<ignore\>** in the **Destination** column of the **Column Mappings** dialog box for columns that you don't want to copy.  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics/TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
> [!NOTE]  
>  The purpose of the   
>             [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard is to copy data from a source to a destination. The wizard can also create a destination database and destination tables for you. However, if you have to copy multiple databases or tables, or other kinds of database objects, use the Copy Database Wizard instead. For more info, see   
>             [Use the Copy Database Wizard](../../Topics/TopicNameNotContainA/Use-the-Copy-Database-Wizard.md).  
  
## Screen shots  
 The following screen shot shows the **Select Source Tables and Views** page of the Wizard after selecting the **Copy data from one or more tables or views** option on the **Specify Table Copy or Query** page. In this screen shot, the user has entered a new name for the destination table.  
  
 ![Select tables page of the Import and Export Wizard](../../Topics/TopicNameNotContainA/images/Select-tables1.png "Select)  
  
 The following screen shot shows the **Select Source Tables and Views** page of the Wizard after selecting the **Write a query to specify the data to transfer** option on the **Specify Table Copy or Query** page. In this screen shot, the user has entered a new name for the destination table.  
  
 ![Select tables page of the Import and Export Wizard](../../Topics/TopicNameNotContainA/images/Select-tables2.png "Select)  
  
## Tables and views List  
 **Source**  
 Using the check boxes, select from the list of available tables and views to copy to the destination. If you select a source table or view and perform no other action, the schema and data from the source are copied without changes.  
  
 **Destination**  
 Select a destination table from the list for each source table, or enter the name of a new table that you want the wizard to create.  
  
 If you specified a new table, you can click **Edit mappings** to display the **Column Mappings** dialog box.  In the **Column Mappings** dialog box, you can review the new destination columns, and you can click **Edit SQL** to review and customize the CREATE TABLE statement that the wizard will run.  
  
> [!NOTE]  
>  If you pause at this point in the wizard to create a new table in the destination database by using an external tool (such as  [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]), the new table is not immediately visible in the list of available destination tables. To refresh the list of destination tables, step back to the **Choose a Destination** page, re-select the destination database, then step forward again to the **Select Source Tables and Views** page.  
  
## What's next?  
 After you select the existing tables and views to copy or review the query that you provided, the next page depends on the option that you choose.  
  
-   Optionally click **Edit mappings** to display the **Column Mappings** dialog box for the selected table. Use the **Column Mappings** dialog box to specify destination columns to receive the copied data. You can copy only a subset of columns by selecting <ignore\> in the **Destination** column of the **Column Mappings** dialog box for columns that you don't want to copy.  
  
-   Optionally click **Preview** to preview up to 200 rows of sample data in the **Preview Data** dialog box. This helps you to confirm that the wizard is going to copy the data that you want to copy.  
  
     After you preview the data, you may want to change the options that you selected on previous pages of the wizard. To make these changes, on the **Select Source Tables and Views** page, click **Back** to return to previous pages where you can change your selections.  
  
-   If you don't display one of the optional dialog boxes, the next page is **Save and Execute Package**. On this page, you specify whether you want to run the copy operation immediately. Depending on your configuration, you may also be able to save the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package created by the wizard  to customize it and to reuse it. For more info, see [Save and Run Package (SQL Server Import and Export Wizard)](../../Topics/TopicNameNotContainA/Save-and-Run-Package--SQL-Server-Import-and-Export-Wizard-.md).