---
title: How FOR JSON escapes special characters and control characters (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
---
# How FOR JSON escapes special characters and control characters (SQL Server)
  This topic describes how the **FOR JSON** clause escapes special characters and represents control characters in the JSON output.  
  
## Escaping of special characters  
 The **FOR JSON** clause escapes special characters in the JSON output with `\`, as shown in the following table. This escaping occurs both in the names of properties and in their values.  
  
|**Special character**|**Encoded sequence**|  
|---------------------------|--------------------------|  
|Quotation mark \("\)|\\"|  
|Backslash \(\\\)|\\\\|  
|Slash \(\/\)|\\\/|  
|Backspace|\\b|  
|Form feed|\\f|  
|New line|\\n|  
|Carriage return|\\r|  
|Horizontal tab|\\t|  
  
## Control characters  
 The **FOR JSON** clause represents control characters in the JSON output in `\u<code>` format, as shown in the following table.  
  
|**Control character**|**Encoded sequence**|  
|---------------------------|--------------------------|  
|CHAR\(0\)|\\u0000|  
|CHAR\(1\)|\\u0001|  
|…|…|  
|CHAR\(31\)|\\u001f|  
  
## Example  
 Here's an example of a **FOR JSON** clause that includes both escaping and control characters.  
  
 Query:  
  
```tsql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 Result:  
  
```json  
{  
   "KEY\\\t\/\"":"VALUE\\\t\/\r\n\"",  
   "0":"\u0000",  
   "1":"\u0001",  
  "31":"\u001f“  
}  
```  
  
## See Also  
 [Format Query Results as JSON with FOR JSON &#40;SQL Server&#41;](../Topic/Format%20Query%20Results%20as%20JSON%20with%20FOR%20JSON%20\(SQL%20Server\).md)  
  
  