---
title: OLE DB Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
---
# OLE DB Destination
  The OLE DB destination loads data into a variety of OLE DB\-compliant databases using a database table or view or an SQL command. For example, the OLE DB source can load data into tables in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Office Access and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases.  
  
> [!NOTE]  
>  If the data source is [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Office Excel 2007, the data source requires a different connection manager than earlier versions of Excel. For more information, see [Connect to an Excel Workbook](../../Topics\TopicNameNotContainA/Connect-to-an-Excel-Workbook.md).  
  
 The OLE DB destination provides five different data access modes for loading data:  
  
-   A table or view. You can specify an existing table or view, or you create a new table.  
  
-   A table or view using fast\-load options. You can specify an existing table or create a new table.  
  
-   A table or view specified in a variable.  
  
-   A table or view specified in a variable using fast\-load options.  
  
-   The results of an SQL statement.  
  
> [!NOTE]  
>  The OLE DB destination does not support parameters. If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation. For more information, see [OLE DB Command Transformation](../../Topics\TopicNameNotContainA/OLE-DB-Command-Transformation.md).  
  
 When the OLE DB destination loads data that uses a double\-byte character set \(DBCS\), the data may be corrupted if the data access mode does not use the fast load option and if the OLE DB connection manager uses the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(SQLOLEDB\). To ensure the integrity of DBCS data you should configure the OLE DB connection manager to use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client, or use one of the fast\-load access modes: **Table or view \- fast load** or **Table name or view name variable \- fast load**. Both options are available from the **OLE DB Destination Editor** dialog box. When programming the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] object model, you should set the AccessMode property to **OpenRowset Using FastLoad**, or **OpenRowset Using FastLoad From Variable**.  
  
> [!NOTE]  
>  If you use the **OLE DB Destination Editor** dialog box in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer to create the destination table into which the OLE DB destination inserts data, you may have to select the newly created table manually. The need for manual selection occurs when an OLE DB provider, such as the OLE DB provider for DB2, automatically adds schema identifiers to the table name.  
  
> [!NOTE]  
>  The CREATE TABLE statement that the **OLE DB Destination Editor** dialog box generates may require modification depending on the destination type. For example, some destinations do not support the data types that the CREATE TABLE statement uses.  
  
 This destination uses an OLE DB connection manager to connect to a data source and the connection manager specifies the OLE DB provider to use. For more information, see [OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md).  
  
 An [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project also provides the data source object from which you can create an OLE DB connection manager, to make data sources and data source views available to the OLE DB destination.  
  
 An OLE DB destination includes mappings between input columns and columns in the destination data source. You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors can occur if no input columns are mapped to the destination columns. For example, if a destination column does not allow null values, an input column must be mapped to that column. In addition, the data types of mapped columns must be compatible. For example, you cannot map an input column with a string data type to a destination column with a numeric data type.  
  
 The OLE DB destination has one regular input and one error output.  
  
 For more information about data types, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Fast Load Options  
 If the OLE DB destination uses a fast\-load data access mode, you can specify the following fast load options in the user interface, **OLE DB Destination Editor**, for the destination:  
  
-   Keep identity values from the imported data file or use unique values assigned by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   Retain a null value during the bulk load operation.  
  
-   Check constraints on the target table or view during the bulk import operation.  
  
-   Acquire a table\-level lock for the duration of the bulk load operation.  
  
-   Specify the number of rows in the batch and the commit size.  
  
 Some fast load options are stored in specific properties of the OLE DB destination. For example, FastLoadKeepIdentity specifies whether to keep identify values, FastLoadKeepNulls specifies whether to keep null values, and FastLoadMaxInsertCommitSize specifies the number of rows to commit as a batch. Other fast load options are stored in a comma\-separated list in the FastLoadOptions property. If the OLE DB destination uses all the fast load options that are stored in FastLoadOptions and listed in the **OLE DB Destination Editor** dialog box, the value of the property is set to **TABLOCK, CHECK\_CONSTRAINTS, ROWS\_PER\_BATCH\=1000**. The value 1000 indicates that the destination is configured to use batches of 1000 rows.  
  
> [!NOTE]  
>  Any constraint failure at the destination causes the entire batch of rows defined by FastLoadMaxInsertCommitSize to fail.  
  
 In addition to the fast load options exposed in the **OLE DB Destination Editor** dialog box,you can configure the OLE DB destination to use the following bulk load options by typing the options in FastLoadOptions property in the **Advanced Editor** dialog box.  
  
|Fast load option|Description|  
|----------------------|-----------------|  
|KILOBYTES\_PER\_BATCH|Specifies the size in kilobytes to insert. The option has the form **KILOBYTES\_PER\_BATCH** \= \<positive integer value**\>**.|  
|FIRE\_TRIGGERS|Specifies whether triggers fire on the insert table. The option has the form **FIRE\_TRIGGERS**. The presence of the option indicates that triggers fire.|  
|ORDER|Specifies how the input data is sorted. The option has the form ORDER \<column name\> ASC&#124;DESC. Any number of columns may be listed and it is optional to include the sort order. If sort order is omitted, the insert operation assumes the data is unsorted.<br /><br /> Note: Performance can be improved if you use the ORDER option to sort the input data according to the clustered index on the table.|  
  
 The [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] keywords are traditionally typed using uppercase letters, but the keywords are not case sensitive.  
  
 To learn more about fast load options, see [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md).  
  
## Troubleshooting the OLE DB Destination  
 You can log the calls that the OLE DB destination makes to external data providers. You can use this logging capability to troubleshoot the saving of data to external data sources that the OLE DB destination performs. To log the calls that the OLE DB destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level. For more information, see [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md).  
  
## Configuring the OLE DB Destination  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **OLE DB Destination Editor** dialog box, click one of the following topics:  
  
-   [OLE DB Destination Editor &#40;Connection Manager Page&#41;](../Topic/OLE%20DB%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [OLE DB Destination Editor &#40;Mappings Page&#41;](../Topic/OLE%20DB%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
-   [OLE DB Destination Editor &#40;Error Output Page&#41;](../Topic/OLE%20DB%20Destination%20Editor%20\(Error%20Output%20Page\).md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [OLE DB Custom Properties](../../Topics\TopicNameNotContainA/OLE-DB-Custom-Properties.md)  
  
 For more information about how to set properties, click one of the following topics:  
  
-   [Load Data by Using the OLE DB Destination](../../Topics\TopicNameNotContainA/Load-Data-by-Using-the-OLE-DB-Destination.md)  
  
-   [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md)  
  
## Related Content  
 [OLE DB Source](../../Topics\TopicNameNotContainA/OLE-DB-Source.md)  
  
 [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md)  
  
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  