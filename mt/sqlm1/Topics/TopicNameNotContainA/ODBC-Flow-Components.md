---
title: ODBC Flow Components
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf751f1e-2348-4a77-904c-bd92c0d7d0ae
---
# ODBC Flow Components
  This topic describes the concepts necessary for creating an ODBC data flow using [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)]  
  
 The Connector for Open Database Connectivity \(ODBC\) by Attunity for [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)] helps SSIS developers easily create packages that load and unload data from ODBC\-supported databases.  
  
 The ODBC Connector is designed to achieve optimal performance when loading data into or unloading data from an ODBC\-supported database in the context of [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)].  
  
## Benefits  
 The ODBC source and ODBC destination for [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)] provides a competitive edge for SSIS in projects dealing with loading data into or unloading data from ODBC\-supported databases.  
  
 Both the ODBC source and ODBC destination enable high performance data integration with ODBC\-enabled databases. Both components can be configured to work with row\-wise parameter array bindings for high\-functioning ODBC providers that support this mode of binding and single\-row parameter bindings for low\-functioning ODBC providers.  
  
## Getting Started with the ODBC Source and Destination  
 Before you can set up packages that use [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)], you must make sure that the following are available.  
  
-   [ODBC Source](../../Topics\TopicNameNotContainA/ODBC-Source.md)  
  
-   [ODBC Destination](../../Topics\TopicNameNotContainA/ODBC-Destination.md)  
  
 The ODBC source and ODBC destination provide an easy way to unload and load data and transfer data from an ODBC\-supported source database to an ODBC\-supported destination database.  
  
 To use the source or destination to load or unload data, open a new [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)] Project in the [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)]. Then drag the source or destination onto the design surface of the [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)].  
  
-   The ODBC source component reads data from the source ODBC\-supported database.  
  
 You can connect the ODBC source to any destination or transform component supported by SSIS.  
  
 **See also:**  
  
 ODBC Source  
  
 ODBC Source Editor \(Connection Manager Page\)  
  
 ODBC Source Editor \(Error Output Page\)  
  
-   The ODBC destination loads data into an ODBC\-supported database. You connect the destination to any source or transform component supported by SSIS.  
  
 **See also:**  
  
 ODBC Destination  
  
 ODBC Destination Editor \(Connection Manager Page\)  
  
 ODBC Destination Editor \(Error Output Page\)  
  
## Operating Scenarios  
 This section describes some of the main uses for the ODBC source and destination components.  
  
### Bulk Copy Data from SQL Server tables to any ODBC\-Supported database table  
 You can use the components to bulk copy data from one or more [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tables to a single ODBC\-supported database table.  
  
 The following example shows how to create an SSIS Data Flow Task that extracts data from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table and loads it into a DB2 table.  
  
-   Create an [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)] Project in the [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)].  
  
-   Create an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database that contains the data you want to copy.  
  
-   Create an ODBC connection manager that uses a locally installed DB2 ODBC driver with a DSN pointing to a local or remote DB2 database. This database is where the data from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database is loaded.  
  
-   Drag an OLE DB source to the design surface, then configure the source to get the data from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database and table with the data you are going to extract. Use the OLE DB connection manager you created previously.  
  
-   Drag an ODBC destination to the design surface, connect the source output to the ODBC destination, then configure the destination to load the data into the DB2 table with the data you extract from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database. Use the ODBC connection manager you created previously.  
  
### Bulk Copy Data from ODBC\-supported database tables to any SQL Server table  
 You can use the components to bulk copy data from one or more ODBC\-supported database tables to a single [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database table.  
  
 The following example shows how to create an SSIS Data Flow Task that extracts data from a Sybase database table and loads it into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database table.  
  
-   Create an [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)] Project in the [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)]  
  
-   Create an ODBC connection manager that uses a locally installed Sybase ODBC driver with a DSN pointing to a local or remote Sybase database. This database is where the data is extracted.  
  
-   Create an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database where you want to load the data.  
  
-   Drag an ODBC source to the design surface, then configure the source to get the data from the Sybase table with the data you are going to copy. Use the ODBC connection manager you created previously.  
  
-   Drag an OLE DB destination to the design surface, connect the source output to the OLE DB destination, then configure the destination to load the data into the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table with the data you extract from the Sybase database. Use the OLE DB connection manager you created previously.  
  
## Supported Data Types  
 The ODBC Bulk SSIS components support all built\-in ODBC data types, including support for large objects \(CLOBs and BLOBs\).  
  
There is no data type support for extensible C types as described in the ODBC 3.8 specifications.The following table describes which SSIS data types are used for each ODBC SQL type. An SSIS developer can override the default mapping and specify a different SSIS data type for input\/output columns without impacting the performance for the required data conversions.  
  
|ODBC SQL Type|SSIS Data Type|Comments|  
|-----------------|------------------|------------|  
|SQL\_BIT|DT\_BOOL||  
|SQL\_TINYINT|DT\_I1<br /><br />DT\_UI1|SQL data types are mapped to SSIS unsigned types \(DT\_UI1, DT\_UI2, DT\_UI4, DT\_UI8\) when the ODBC driver sets the UNSIGNED\_ATTRIBUTE to SQL\_TRUE for that SQL data type.|  
|SQL\_SMALLINT|DT\_I2<br /><br />DT\_UI2|SQL data types are mapped to SSIS unsigned types \(DT\_UI1, DT\_UI2, DT\_UI4, DT\_UI8\) when the ODBC driver sets the UNSIGNED\_ATTRIBUTE to SQL\_TRUE for that SQL data type.|  
|SQL\_INTEGER|DT\_I4<br /><br />DTUI4|SQL data types are mapped to SSIS unsigned types \(DT\_UI1, DT\_UI2, DT\_UI4, DT\_UI8\) when the ODBC driver sets the UNSIGNED\_ATTRIBUTE to SQL\_TRUE for that SQL data type.|  
|SQL\_BIGINT|DT\_I8<br /><br />DT\_UI8|SQL data types are mapped to SSIS unsigned types \(DT\_UI1, DT\_UI2, DT\_UI4, DT\_UI8\) when the ODBC driver sets the UNSIGNED\_ATTRIBUTE to SQL\_TRUE for that SQL data type.|  
|SQL\_DOUBLE|DT\_R8|  
|SQL\_FLOAT|DT\_R8|  
|SQL\_REAL|DT\_R4|  
|SQL\_NUMERIC \(p,s\)|DT\_NUMERIC \(p,s\)|The numeric data type is mapped to DT\_NUMERIC when P is greater than or equal to 38 and S is greater than or equal to 0 and S is less than or equal to P.|  
||DT\_R8|The numeric data type is mapped to DT\_R8 when at least one of the following is true:<br /><br />Precision is greater than 38<br /><br />Scale is less than zero<br /><br />Scale is greater than 38<br /><br />Scale is greater than Precision|  
||DT\_CY|The numeric data type is mapped to DT\_CY when it is declared as a money data type.|  
|SQL\_DECIMAL \(p,s\)|DT\_NUMERIC \(p,s\)|The decimal data type is mapped to DT\_NUMERIC when P is greater than or equal to 38 and S is greater than or equal to 0 and S is less than or equal to P.|  
||DT\_R8|The decimal data type is mapped to DT\_R8 when at least one of the following is true:<br /><br />Precision is greater than 38<br /><br />Scale is less than zero<br /><br />Scale is greater than 38<br /><br />Scale is greater than Precision|  
||DT\_CY|The decimal data type is mapped to DT\_CY when it is declared as a money data type.|  
|SQL\_DATE<br /><br />SQL\_TYPE\_DATE|DT\_DBDATE|  
|SQL\_TIME<br /><br />SQL\_TYPE\_TIME|DT\_DBTIME|  
|SQL\_TIMESTAMP<br /><br />SQL\_TYPE\_TIMESTAMP|DT\_DBTIMESTAMP<br /><br />DT\_DBTIMESTAMP2|SQL\_TIMESTAMP data types are mapped to DT\_DBTIMESTAMP2 if  scale is greater than 3. In all other cases, they are mapped to DT\_DBTIMESTAMP.|  
|SQL\_CHAR<br /><br />SQLVARCHAR|DT\_STR<br /><br />DT\_WSTR<br /><br />DT\_TEXT<br /><br />DT\_NTEXT|DT\_STR is used if the column length is less than or equal to 8000 and the **ExposeStringsAsUnicode** property is false.<br /><br />DT\_WSTR is used if the column length is less than or equal to 8000 and the **ExposeStringsAsUnicode** property is true.<br /><br />DT\_TEXT is used if the column length is greater than 8000 and the **ExposeStringsAsUnicode** property is false.<br /><br />DT\_NTEXT is used if the column length is greater than 8000 and the **ExposeStringsAsUnicode** property is true.|  
|SQL\_LONGVARCHAR|DT\_TEXT<br /><br />DT\_NTEXT|DT\_NTEXT is used if the **ExposeStringsAsUnicode** property is true.|  
|SQL\_WCHAR<br /><br />SQL\_WVARCHAR|DT\_WSTR<br /><br />DT\_NTEXT|DT\_WSTR is used if the column length is less than or equal to 4000.<br /><br />DT\_NTEXT is used if the column length is greater than 4000.|  
|SQL\_WLONGVARCHAR|DT\_NTEXT|  
|SQL\_BINARY|DT\_BYTE<br /><br />DT\_IMAGE|DT\_BYTES is used if the column length is less than or equal to 8000.<br /><br />DT\_IMAGE if the column length is greater than 8000.|  
|SQL\_LONGVARBINARY|DT\_IMAGE|  
|SQL\_GUID|DT\_GUID|  
|SQL\_INTERVAL\_YEAR<br /><br />SQL\_INTERVAL\_MONTH<br /><br />SQL\_INTERVAL\_DAY<br /><br />SQL\_INTERVAL\_HOUR<br /><br />SQL\_INTERVAL\_MINUTE<br /><br />SQL\_INTERVAL\_SECOND<br /><br />SQL\_INTERVAL\_YEAR\_TO\_MONTH<br /><br />SQL\_INTERVAL\_DAY\_TO\_HOUR<br /><br />SQL\_INTERVAL\_DAY\_TO\_MINUTE<br /><br />SQL\_INTERVAL\_DAY\_TO\_SECOND<br /><br />SQL\_INTERVAL\_HOUR\_TO\_MINUTE<br /><br />SQL\_INTERVAL\_HOUR\_TO\_SECOND<br /><br />SQL\_INTERVAL\_MINUTE\_TO\_SECOND|DT\_WSTR|  
|Provider Specific Data Types|DT\_BYTES<br /><br />DT\_IMAGE|DT\_BYTES is used if the column length is less than or equal to 8000.<br /><br />DT\_IMAGE is used if the column length is zero or greater than 8000.|  
  
## In This Section  
  
-   [ODBC Source](../../Topics\TopicNameNotContainA/ODBC-Source.md)  
  
-   [ODBC Destination](../../Topics\TopicNameNotContainA/ODBC-Destination.md)  
  
 