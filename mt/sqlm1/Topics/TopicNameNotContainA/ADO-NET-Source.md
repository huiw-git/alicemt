---
title: ADO NET Source
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
---
# ADO NET Source
  The ADO NET source consumes data from a .NET provider and makes the data available to the data flow.  
  
 You can use the ADO NET source to connect to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssSDSFull](../../Token\Other/ssSDSfull_md.md)]. Connecting to [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] by using OLE DB is not supported. For more information about [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)], see [General Guidelines and Limitations \(Windows Azure SQL Database\)](http://go.microsoft.com/fwlink/?LinkId=248228).  
  
## Data Type Support  
 The source converts any data type that does not map to a specific [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data type to the DT\_NTEXT [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data type. This conversion occurs even if the data type is **System.Object**.  
  
 You can change the DT\_NTEXT data type to the DT\_WSTR data type, or the change DT\_WSTR to DT\_NTEXT. You change data types by setting the **DataType** property in the **Advanced Editor** dialog box of the ADO NET source. For more information, see [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md).  
  
 The DT\_NTEXT data type can also be converted to the DT\_BYTES or DT\_STR data type by using a Data Conversion transformation after the ADO NET source. For more information, see [Data Conversion Transformation](../../Topics\TopicNameNotContainA/Data-Conversion-Transformation.md).  
  
 In [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], the date data types, DT\_DBDATE, DT\_DBTIME2, DT\_DBTIMESTAMP2, and DT\_DBTIMESTAMPOFFSET, map to certain date data types in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. You can configure the ADO NET source to convert the date data types from those that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses to those that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] uses. To configure the ADO NET source to convert these date data types, set the **Type System Version** property of the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager to **Latest**. \(The **Type System Version** property is on the **All** page of the **Connection Manager** dialog box. To open the **Connection Manager** dialog box, right\-click the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager, and then click **Edit**.\)  
  
> [!NOTE]  
>  If the **Type System Version** property for the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager is set to **SQL Server 2005**, the system converts the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] date data types to DT\_WSTR.  
  
 The system converts user\-defined data types \(UDTs\) to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] binary large objects \(BLOB\) when the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager specifies the provider as the .NET Data Provider for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(SqlClient\). The system applies the following rules when it converts the UDT data type:  
  
-   If the data is a non\-large UDT, the system converts the data to DT\_BYTES.  
  
-   If the data is a non\-large UDT, and the **Length** property of the column on the database is set to \-1 or a value greater than 8,000 bytes, the system converts the data to DT\_IMAGE.  
  
-   If the data is a large UDT, the system converts the data to DT\_IMAGE.  
  
    > [!NOTE]  
    >  If the ADO NET source is not configured to use error output, the system streams the data to the DT\_IMAGE column in chunks of 8,000 bytes. If the ADO NET source is configured to use error output, the system passes the whole array of bytes to the DT\_IMAGE column. For more information about how to configure components to use error output, see [Error Handling in Data](../../Topics\TopicNameNotContainA/Error-Handling-in-Data.md).  
  
 For more information about the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data types, supported data type conversions, and data type mapping across certain databases including [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 For information about mapping [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data types to managed data types, see [Working with Data Types in the Data Flow](../Topic/Working%20with%20Data%20Types%20in%20the%20Data%20Flow.md).  
  
## ADO NET Source Troubleshooting  
 You can log the calls that the ADO NET source makes to external data providers. You can use this logging capability to troubleshoot the loading of data from external data sources that the ADO NET source performs. To log the calls that the ADO NET source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level. For more information, see [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md).  
  
## ADO NET Source Configuration  
 You configure the ADO NET source by providing the SQL statement that defines the result set. For example, an ADO NET source that connects to the [!INCLUDE[ssSampleDBUserInputNonLocal](../../Token\Other/ssSampleDBUserInputNonLocal_md.md)] database and uses the SQL statement `SELECT * FROM Production.Product` extracts all the rows from the **Production.Product** table and provides the dataset to a downstream component.  
  
> [!NOTE]  
>  When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.  
  
> [!NOTE]  
>  If you use an SQL statement to execute a stored procedure and the package fails with the following error, you may be able to resolve the error by adding the **SET FMTONLY OFF** statement before the exec statement.  
>   
>  **Column \<column\_name\> cannot be found at the datasource.**  
  
 The ADO NET source uses an [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager to connect to a data source, and the connection manager specifies the .NET provider. For more information, see [ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/ADO.NET-Connection-Manager.md).  
  
 The ADO NET source has one regular output and one error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [ADO NET Custom Properties](../../Topics\TopicNameNotContainA/ADO-NET-Custom-Properties.md)  
  
 For more information about how to set properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [DataReader Destination](../../Topics\TopicNameNotContainA/DataReader-Destination.md)   
 [ADO NET Destination](../../Topics\TopicNameNotContainA/ADO-NET-Destination.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  