---
title: How FOR JSON converts SQL Server data types to JSON data types (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
---
# How FOR JSON converts SQL Server data types to JSON data types (SQL Server)
  The **FOR JSON** clause uses the following rules to convert SQL data types to JSON types in the JSON output.  
  
|Category|SQL type|JSON type|  
|--------------|--------------|---------------|  
|Character & string types|\(n\)\(var\)\(char\)|string|  
|Numeric types|int, bigint, float, decimal, numeric|number|  
|Bit type|bit|Boolean \(true or false\)|  
|Date & time types|date, datetime, datetime2, time, datetimeoffset|string|  
|Binary types|varbinary, binary, image, timestamp, rowversion|BASE64\-encoded string|  
|CLR types|CLR, geometry, geography|Not supported. These types return an error.<br /><br /> Cast or convert the data to a supported JSON type, or use a CLR property or method in the SELECT list – for example, **ToString\(\)** for any CLR type, or **STAsText\(\)** for the geometry type. The type of the JSON output value is derived from the type of the property or method that you use in the SELECT statement.|  
|Other types|uniqueidentifier, money|string|  
  
## See Also  
 [Format Query Results as JSON with FOR JSON &#40;SQL Server&#41;](../Topic/Format%20Query%20Results%20as%20JSON%20with%20FOR%20JSON%20\(SQL%20Server\).md)  
  
  