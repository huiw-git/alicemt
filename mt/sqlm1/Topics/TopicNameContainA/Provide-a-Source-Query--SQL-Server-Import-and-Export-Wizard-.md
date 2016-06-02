---
title: Provide a Source Query (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
---
# Provide a Source Query (SQL Server Import and Export Wizard)
  If you specified that you wanted to provide a query to select the data to copy, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Provide a Source Query**. On this page, you write and test the SQL query that selects the data to copy from the data source to the destination.  
  
 When you select **Write a query to specify the data to transfer** on the **Select Table Copy or Query** page, you can only copy the results of one query to one destination table.  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
> [!NOTE]  
>  The purpose of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard is to copy data from a source to a destination. The wizard can also create a destination database and destination tables for you. However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead. For more info, see [Use the Copy Database Wizard](../../Topics\TopicNameNotContainA/Use-the-Copy-Database-Wizard.md).  
  
## Screen shot  
 The following screen shot shows the **Provide a Source Query** page of the Wizard.  
  
 ![Source query page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Source-query.png "Source query")  
  
## Options on this page  
 **SQL statement**  
 Type a SELECT query to retrieve specific rows of data from the source database.  
  
 For example, the following query statement retrieves the **SalesPersonID**, **SalesQuota**, and **SalesYTD** from the AdventureWorks database for sales persons whose commission percentage is more than 1.5 percent.  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 For more examples of SELECT queries, see [SELECT Examples &#40;Transact-SQL&#41;](../Topic/SELECT%20Examples%20\(Transact-SQL\).md).  
  
 **Parse**  
 Checks the syntax of the SQL statement in the **SQL statement** text box.  
  
> [!NOTE]  
>  If the time that\'s required to check the syntax of the statement exceeds the timeout value of 30 seconds, parsing stops and raises an error. You won't be able to move past this page of the wizard until parsing succeeds. One solution is to create a database view based on the query, and to query the view from the wizard, instead of entering the query text directly.  
  
 **Browse**  
 Select a saved file that contains a SQL statement by using the **Open** dialog box. Selecting a file copies the text from the file into the **SQL statement** text box.  
  
## What's next?  
 After you write and test the SQL query that selects the data to copy, the next page depends on the destination for your data.  
  
-   For most destinations the next page is **Select Source Tables and Views**. On this page, you review the query that you provided and optionally choose columns to copy and preview sample data. For more info, see [Select Source Tables and Views &#40;SQL Server Import and Export Wizard&#41;](../Topic/Select%20Source%20Tables%20and%20Views%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
-   If your destination is a flat file, the next page is **Configure Flat File Destination**. On this page, you specify formatting options for the destination flat file. \(After you configure the flat file, the next page is **Select Source Tables and Views**.\) For more info, see [Configure Flat File Destination &#40;SQL Server Import and Export Wizard&#41;](../Topic/Configure%20Flat%20File%20Destination%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  