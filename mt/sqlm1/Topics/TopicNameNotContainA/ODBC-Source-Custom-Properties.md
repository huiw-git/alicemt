---
title: ODBC Source Custom Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
---
# ODBC Source Custom Properties
  The following table describes the custom properties of the ODBC source. All properties can be set from SSIS property expressions.  
  
|Property name|Data Type|Description|  
|-------------------|---------------|-----------------|  
|Connection|ODBC Connection|An ODBC connection to access the source database.|  
|AccessMode|Integer \(enumeration\)|The mode used to access the database. The possible values are Table Name \(0\) and SQL Command \(1\).<br /><br /> The default is Table Name \(0\).|  
|BatchSize|Integer|The size of the batch for bulk extraction. This is the number of records extracted as an array. If the selected ODBC provider does not support arrays, the batch size is 1.|  
|BindCharColumnAs|Integer \(enumeration\)|This property determines how the ODBC source binds columns with multiple\-byte string types such as SQL\_CHAR, SQL\_VARCHAR, or SQL\_LONGVARCHAR.<br /><br /> The possible values are Unicode \(0\), which binds the columns as SQL\_C\_WCHAR, and ANSI \(1\), which binds the columns as SQL\_C\_CHAR\). The default is Unicode \(0\).<br /><br /> **Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.|  
|BindNumericAs|Integer \(enumeration\)|This property determines how the ODBC source binds columns with numeric data with data types SQL\_TYPE\_NUMERIC and SQL\_TYPE\_DECIMAL.<br /><br /> The possible options are Char \(0\), which binds the columns as SQL\_C\_CHAR and Numeric \(1\), which binds the columns as SQL\_C\_NUMERIC. The default value is Char \(0\).<br /><br /> **Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.|  
|DefaultCodePage|Integer|The code page to use for string output columns.<br /><br /> **Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.|  
|ExposeCharColumnsAsUnicode|Boolean|This property determines how the component exposes CHAR columns. The default value is False, which indicates that CHAR columns are exposed as multi\-byte strings \(DT\_STR\). If True, CHAR columns are exposed as wide strings \(DT\_WSTR\).<br /><br /> **Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.|  
|FetchMethod|Integer \(enumeration\)|The method used for getting the data. The possible options are Row by row \(0\) and Batch \(1\). The default value is Batch \(1\).<br /><br /> For more information about these options, see [ODBC Source](../../Topics\TopicNameNotContainA/ODBC-Source.md).<br /><br /> **Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.|  
|SqlCommand|String|The SQL command to be executed when AccessMode is set to SQL Command.|  
|StatementTimeout|Integer|The number of seconds to wait for an SQL statement to execute before returning, with an error, to the application. The default value is 120. A value of 0 indicates that the system does not time out.|  
|TableName|String|The name of the table with the data that is being used when AccessMode is set to Table Name.|  
|LobChunckSize|Integer|The chunk size allocation for LOB columns.|  
||||  
  
## See Also  
 [ODBC Source](../../Topics\TopicNameNotContainA/ODBC-Source.md)   
 [ODBC Source Editor &#40;Connection Manager Page&#41;](../Topic/ODBC%20Source%20Editor%20\(Connection%20Manager%20Page\).md)  
  
  