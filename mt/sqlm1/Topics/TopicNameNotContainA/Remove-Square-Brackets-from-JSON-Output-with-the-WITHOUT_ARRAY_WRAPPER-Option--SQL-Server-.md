---
title: Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
---
# Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option (SQL Server)
  To remove the square brackets that surround the JSON output of the **FOR JSON** clause by default, specify the **WITHOUT\_ARRAY\_WRAPPER** option. Use this option to generate a single JSON object as output.  
  
 If you don't specify this option, the JSON output is enclosed within square brackets.  
  
## Examples  
 The following example shows the output of the **FOR JSON** clause with and without the **WITHOUT\_ARRAY\_WRAPPER** option.  
  
 **Query**  
  
```tsql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Result** With the **WITHOUT\_ARRAY\_WRAPPER** option  
  
```json  
{ "year":2015, "month":12, "day":15 }  
```  
  
 **Result** Without the **WITHOUT\_ARRAY\_WRAPPER** option  
  
```json  
[ { "year":2015, "month":12, "day":15 } ]  
```  
  
 Here's another example of a **FOR JSON** clause with the **WITHOUT\_ARRAY\_WRAPPER** option..  
  
 **Query**  
  
```tsql  
SELECT TOP 1 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Result** With the **WITHOUT\_ARRAY\_WRAPPER** option  
  
```json  
{  
    "SalesOrderNumber":"SO43660",  
    "OrderDate":"2011-05-31T00:00:00",  
    "Status":5  
}  
```  
  
 **Result** Without the **WITHOUT\_ARRAY\_WRAPPER** option  
  
```json  
[  
    {  
        "SalesOrderNumber":"SO43660",  
        "OrderDate":"2011-05-31T00:00:00",  
        "Status":5  
    }  
]  
```  
  
## See Also  
 [FOR Clause &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  