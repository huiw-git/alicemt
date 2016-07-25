---
title: "Retrieving Data as a Stream Using the SQLSRV Driver"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17dc9129-04cd-430c-b5b3-82824116425d
caps.latest.revision: 18
manager: jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Retrieving Data as a Stream Using the SQLSRV Driver
Retrieving data as a stream is only available in the SQLSRV driver of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], and is not available in the PDO_SQLSRV driver.  
  
The [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] takes advantage of streams for retrieving large amounts of data. The topics in this section provide details about how to retrieve data as a stream.  
  
The following steps summarize how to retrieve data as a stream:  
  
1.  Prepare and execute a Transact-SQL query with [sqlsrv_query](../content/sqlsrv_query.md) or the combination of [sqlsrv_prepare](../content/sqlsrv_prepare.md)/[sqlsrv_execute](../content/sqlsrv_execute.md).  
  
2.  Use [sqlsrv_fetch](../content/sqlsrv_fetch.md) to move to the next row in the result set.  
  
3.  Use [sqlsrv_get_field](../content/sqlsrv_get_field.md) to retrieve a field from the row. Specify that the data is to be retrieved as a stream by using **SQLSRV_PHPTYPE_STREAM(<encoding>)** as the third parameter in the function call. This table lists the constants used to specify encodings and their descriptions:  
  
    |SQLSRV Constant|Description|  
    |-------------------|---------------|  
    |SQLSRV_ENC_BINARY|Data is returned as a raw byte stream from the server without performing encoding or translation.|  
    |SQLSRV_ENC_CHAR|Data is returned in 8-bit characters as specified in the code page of the Windows locale set on the system. Any multi-byte characters or characters that do not map into this code page are substituted with a single byte question mark (?) character.|  
  
> [!NOTE]  
> Some data types are returned as streams by default. For more information, see [Default PHP Data Types](../content/Default-PHP-Data-Types.md).  
  
## In This Section  
  
|Topic|Description|  
|---------|---------------|  
|[Data Types with Stream Support Using the SQLSRV Driver](../content/Data-Types-with-Stream-Support-Using-the-SQLSRV-Driver.md)|Lists the SQL Server data types that can be retrieved as streams.|  
|[How to: Retrieve Character Data as a Stream Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Character%20Data%20as%20a%20Stream%20Using%20the%20SQLSRV%20Driver.md)|Demonstrates how to retrieve character data as a stream.|  
|[How to: Retrieve Binary Data as a Stream Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Binary%20Data%20as%20a%20Stream%20Using%20the%20SQLSRV%20Driver.md)|Demonstrates how to retrieve binary data as a stream.|  
  
## See Also  
[Retrieving Data](../content/Retrieving-Data.md)  
[Constants &#40;Microsoft Drivers for PHP for SQL Server&#41;](../content/Constants--Microsoft-Drivers-for-PHP-for-SQL-Server-.md)  
  
