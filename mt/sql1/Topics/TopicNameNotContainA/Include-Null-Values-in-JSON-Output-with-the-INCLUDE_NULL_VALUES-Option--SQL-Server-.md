---
title: "Include Null Values in JSON Output with the INCLUDE_NULL_VALUES Option (SQL Server)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: 14
manager: jhubbard
---
# Include Null Values in JSON Output with the INCLUDE_NULL_VALUES Option (SQL Server)
To include null values in the JSON output of the **FOR JSON** clause, specify the **INCLUDE_NULL_VALUES** option.  
  
 If you don't specify the **INCLUDE_NULL_VALUES** option, the JSON output doesn't include properties for values that are null in the query results.  
  
## Examples  
 The following example shows the output of the **FOR JSON** clause with and without the **INCLUDE_NULL_VALUES** option.  
  
|Without the **INCLUDE_NULL_VALUES** option|With the **INCLUDE_NULL_VALUES** option|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Here's another example of a **FOR JSON** clause with the **INCLUDE_NULL_VALUES** option.  
  
 **Query**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES  
```  
  
 **Result**  
  
```json  
[   
   {"name": "John",  "surname": null },  
   {"name": "Jane",  "surname": "Doe"}  
]  
```  
  
## See Also  
 [FOR Clause (Transact-SQL)](assetId:///08a6f084-8f73-4f2a-bae4-3c7513dc99b9)