---
title: Specify Table Copy or Query (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
---
# Specify Table Copy or Query (SQL Server Import and Export Wizard)
  After you provide info about the destination for your data and about how to connect to it, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Specify Table Copy or Query**. On this page, you specify whether you want to copy an entire table or tables, or only certain rows. You can use a graphical interface to select existing database objects to copy, or you can use the Transact\-SQL language to write a more complex query.    
    
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).    
    
> [!NOTE]    
>  The purpose of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard is to copy data from a source to a destination. The wizard can also create a destination database and destination tables for you. However, if you have to copy multiple databases or tables, or other kinds of database objects, use the Copy Database Wizard instead. For more info, see [Use the Copy Database Wizard](../../Topics\TopicNameNotContainA/Use-the-Copy-Database-Wizard.md).    
    
## Screen shot    
 The following screen shot shows the **Specify Table Copy or Query** page of the Wizard.    
    
 ![Table copy or query page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Table-copy-or-query.png "Table copy or query")    
    
## Options on this page    
 **Copy data from one or more tables or views**    
 Select this option if you want to copy all data in the source without filtering or sorting records. You select tables to copy in the **Select Source Tables and Views** dialog box after you click **Next**. For more info, see [Select Source Tables and Views &#40;SQL Server Import and Export Wizard&#41;](../Topic/Select%20Source%20Tables%20and%20Views%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).    
    
 **Write a query to specify the data to transfer**    
 Select this option if you want to filter or sort the source data during the copy operation. The wizard copies only the rows matching the selection criteria. You write a SQL statement to select rows in the **Provide a Source Query** dialog box after you click **Next**. For more info, see [Provide a Source Query &#40;SQL Server Import and Export Wizard&#41;](../Topic/Provide%20a%20Source%20Query%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).    
    
  ## How many tables can I copy?    
 When you select **Copy data from one or more tables or views**, you can copy from one table or view to one destination table, or from multiple tables or views to multiple destination tables.    
    
When you select **Write a query to specify the data to transfer**, you can only copy the results of one query to one destination table.    
    
## Why isn't the Copy option available?    
 When you use a [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] data provider to connect to your data source, the **Copy data from one or more tables or views** option may not be available. This happens when the wizard doesn't have the info necessary to get a list of tables and views from the data source.    
    
 The **Copy data from one or more tables or views** option is available only for those providers that have a ProviderDescription section in the ProviderDescriptors.xml file. \(By default, this file is in \<*drive*\>:\\Program Files\\Microsoft SQL Server\\130\\DTS\\ProviderDescriptors. \) Each ProviderDescription section in this file contains the information that's required to retrieve metadata from the corresponding provider.    
    
 By default, the ProviderDescriptors.xml file contains a ProviderDescription section only for the providers in the following list.    
    
-   .Net Framework Data Provider for SQL Server \(System.Data.SqlClient\)    
    
-   .Net Framework Data Provider for Oracle \(System.Data.OracleClient\)    
    
-   System.Data.OleDb \(which applies to all OLE DB providers\)    
    
-   .Net Framework Data Provider for ODBC \(System.Data.Odbc\)    
    
-   Microsoft Provider for DB2 installed by Microsoft Host Integration Server \(Microsoft.HostIntegration.MsDb2Client.MsDb2Connection\)    
    
 Third\-party developers can make the **Copy data from one or more tables or views** option available for their provider by adding  a ProviderDescriptor section to the ProviderDescriptors.xml file. To review the requirements for the ProviderDescriptor section, see the ProviderDescriptors.xsd schema file which by default is in the same folder as the ProviderDescriptors.xml file.    
    
## What's next?    
 After you specify whether you want to copy an entire table or only certain rows, the next page depends on the option that you chose and on the destination for your data.    
    
-   If you selected **Copy data from one or more tables or views**, for most destinations the next page is **Select Source Tables and Views**. On this page, you select the existing tables and views to copy from the data source to the destination and optionally choose columns and preview sample data. For more info, see [Select Source Tables and Views &#40;SQL Server Import and Export Wizard&#41;](../Topic/Select%20Source%20Tables%20and%20Views%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).    
    
-   If you selected **Copy data from one or more tables or views** and your destination is a flat file, the next page is **Configure Flat File Destination**. On this page, you specify formatting options for the destination flat file. \(After you configure the flat file, the following page is **Select Source Tables and Views**.\) For more info, see [Configure Flat File Destination &#40;SQL Server Import and Export Wizard&#41;](../Topic/Configure%20Flat%20File%20Destination%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).    
    
-   If you selected **Write a query to specify the data to transfer**, the next page is **Provide a Source Query**. On this page, you write and test the SQL statement that selects the data to copy from the data source to the destination. \(After you provide a query, the following page is **Select Source Tables and Views**.\) For more info, see [Provide a Source Query &#40;SQL Server Import and Export Wizard&#41;](../Topic/Provide%20a%20Source%20Query%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).    
    
  