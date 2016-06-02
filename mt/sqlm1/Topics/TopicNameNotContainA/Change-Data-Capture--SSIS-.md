---
title: Change Data Capture (SSIS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4aaba1b-73e5-4187-a97b-61c10069cc5a
---
# Change Data Capture (SSIS)
  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], change data capture offers an effective solution to the challenge of efficiently performing incremental loads from source tables to data marts and data warehouses.  
  
## What is Change Data Capture?  
 Source tables change over time. A data mart or data warehouse that is based on those tables needs to reflect these changes. However, a process that periodically copies a snapshot of the entire source consumes too much time and resources. Alternate approaches that include timestamp columns, triggers, or complex queries often hurt performance and increase complexity. What is needed is a reliable stream of change data that is structured so that it can easily be applied by consumers to target representations of the data. Change data capture in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides this solution.  
  
 The change data capture feature of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] captures insert, update, and delete activity applied to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tables, and makes the details of the changes available in an easily\-consumed, relational format. The change tables used by change data capture contain columns that mirror the column structure of the tracked source tables, along with the metadata needed to understand the changes that have occurred on a row by row basis.  
  
> [!NOTE]  
>  Change data capture is not available in every edition of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
## How Change Data Capture Works in Integration Services  
 An [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package can easily harvest the change data in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases to perform efficient incremental loads to a data warehouse. However, before you can use [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] to load change data, an administrator must enable change data capture on the database and the tables from which you want to capture changes. For more information on how to configure change data capture on a database, see [Enable and Disable Change Data Capture &#40;SQL Server&#41;](../Topic/Enable%20and%20Disable%20Change%20Data%20Capture%20\(SQL%20Server\).md).  
  
 Once an administrator has enabled change data capture on the database, you can create a package that performs an incremental load of the change data. The following diagram shows the steps for creating such a package that performs an incremental load from a single table:  
  
 ![Change Data Capture Package Creation Steps](../../Images\Image\ImageNotContaina/CDC_package_creation.gif "CDC_package_creation")  
  
 As shown in the previous diagram, creating a package that performs an incremental load of changed data involves the following steps:  
  
 **Step 1: Designing the Control Flow**  
 In the control flow in the package, the following tasks need to be defined:  
  
-   Calculate the starting and ending **datetime** values for the interval of changes to the source data that you want to retrieve.  
  
     To calculate these values, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] expressions with **datetime** functions. You then store these endpoints in package variables for use later in the package.  
  
     **For more information:** [Specify an Interval of Change Data](../../Topics\TopicNameNotContainA/Specify-an-Interval-of-Change-Data.md)  
  
-   Determine whether the change data for the selected interval is ready. This step is necessary because the asynchronous capture process might not yet have reached the selected endpoint.  
  
     To determine whether the data is ready, start with a For Loop container to delay execution, if necessary, until the change data for the selected interval is ready. Inside the loop container, use an Execute SQL task to query the time mapping tables maintained by change data capture. Then, use a Script task that calls the **Thread.Sleep** method, or another Execute SQL task with a **WAITFOR** statement, to delay the execution of the package temporarily, if necessary. Optionally, use another Script task to log an error condition or a timeout.  
  
     **For more information:** [Determine Whether the Change Data Is Ready](../../Topics\TopicNameNotContainA/Determine-Whether-the-Change-Data-Is-Ready.md)  
  
-   Prepare the query string that will be used to query for the change data.  
  
     Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.  
  
     **For more information:** [Prepare to Query for the Change Data](../../Topics\TopicNameNotContainA/Prepare-to-Query-for-the-Change-Data.md)  
  
 **Step 2: Setting Up the Query for Change Data**  
 Create the table\-valued function that will query for the data.  
  
 Use [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to develop and save the query.  
  
 **For more information:** [Retrieve and Understand the Change Data](../../Topics\TopicNameNotContainA/Retrieve-and-Understand-the-Change-Data.md)  
  
 **Step 3: Designing the Data Flow**  
 In the data flow of the package, the following tasks need to be defined:  
  
-   Retrieve the change data from the change tables.  
  
     To retrieve the data, use a source component to query the change tables for the changes that fall within the selected interval. The source calls a Transact\-SQL table\-valued function that you must have previously created.  
  
     **For more information:** [Retrieve and Understand the Change Data](../../Topics\TopicNameNotContainA/Retrieve-and-Understand-the-Change-Data.md)  
  
-   Split the changes into inserts, updates, and deletes for processing.  
  
     To split the changes, use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.  
  
     **For more information:** [Process Inserts, Updates, and Deletes](../../Topics\TopicNameNotContainA/Process-Inserts,-Updates,-and-Deletes.md)  
  
-   Apply the inserts, deletes, and updates to the destination.  
  
     To apply the changes to the destination, use a destination component to apply the inserts to the destination. Also, use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination. You can also apply updates and deletes by using destination components to save the rows to temporary tables. Then, use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.  
  
     **For more information:** [Apply the Changes to the Destination](../../Topics\TopicNameNotContainA/Apply-the-Changes-to-the-Destination.md)  
  
### Change Data from Multiple Tables  
 The process outlined in the previous diagram and steps involves an incremental load from a single table. When having to perform an incremental load from multiple tables, the overall process is the same. However, the design of the package needs to be changed to accommodate the processing of multiple tables. For more information on how to create a package that performs an incremental load from multiples tables, see [Perform an Incremental Load of Multiple Tables](../../Topics\TopicNameNotContainA/Perform-an-Incremental-Load-of-Multiple-Tables.md).  
  
## Samples of Change Data Capture Packages  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides two samples that demonstrate how to use change data capture in packages. For more information, see the following topics:  
  
-   [Readme\_Change Data Capture for Specified Interval Package Sample](http://go.microsoft.com/fwlink/?LinkId=133507)  
  
-   [Readme\_Change Data Capture since Last Request Package Sample](http://go.microsoft.com/fwlink/?LinkId=133508)  
  
## Related Tasks  
  
-   [Specify an Interval of Change Data](../../Topics\TopicNameNotContainA/Specify-an-Interval-of-Change-Data.md)  
  
-   [Determine Whether the Change Data Is Ready](../../Topics\TopicNameNotContainA/Determine-Whether-the-Change-Data-Is-Ready.md)  
  
-   [Prepare to Query for the Change Data](../../Topics\TopicNameNotContainA/Prepare-to-Query-for-the-Change-Data.md)  
  
-   [Create the Function to Retrieve the Change Data](../../Topics\TopicNameNotContainA/Create-the-Function-to-Retrieve-the-Change-Data.md)  
  
-   [Retrieve and Understand the Change Data](../../Topics\TopicNameNotContainA/Retrieve-and-Understand-the-Change-Data.md)  
  
-   [Process Inserts, Updates, and Deletes](../../Topics\TopicNameNotContainA/Process-Inserts,-Updates,-and-Deletes.md)  
  
-   [Apply the Changes to the Destination](../../Topics\TopicNameNotContainA/Apply-the-Changes-to-the-Destination.md)  
  
-   [Perform an Incremental Load of Multiple Tables](../../Topics\TopicNameNotContainA/Perform-an-Incremental-Load-of-Multiple-Tables.md)  
  
## Related Content  
 Blog entry, [SSIS Design Pattern – Incremental Load](http://go.microsoft.com/fwlink/?LinkId=217679), on sqlblog.com  
  
  