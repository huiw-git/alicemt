---
title: Use OPENJSON with an Explicit Schema (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c1c3bfb-e1ad-4659-b94f-722b0848d5a2
---
# Use OPENJSON with an Explicit Schema (SQL Server)
  Use **OPENJSON** with an explicit schema to return a table that's formatted as you specify in the WITH clause.  
  
 Here are some examples that use **OPENJSON** with an explicit schema. For more info and more  examples, see [OPENJSON &#40;Transact-SQL&#41;](../Topic/OPENJSON%20\(Transact-SQL\).md).  
  
## Example \- Use the WITH clause to format the output  
 The following query returns the results shown in the following table. Notice how the AS JSON clause causes values to be returned as JSON objects instead of scalar values in col5 and array\_element.  
  
```tsql  
SET @expression = N'{"someObject":   
   {"someArray":  
     [  
         {"k1": 11, "k2": null, "k3": "text"},  
         {"k1": true, "k2": "text2", "k4": { "data": "text4" }},  
         {"k1": 31, "k2": 32},  
         {"k1": 41, "k2": null, "k4": { "data": false }}     
      ]  
   }  
}  
  
SELECT * FROM  
OPENJSON(@expression, N'lax $.someObject.someArray')  
WITH ( k1 int,   
                k2 varchar(100),  
                col3 varchar(6) N'$.k3',  
                col4 varchar(10) N'lax $.k4.data',  
                col5 varchar(MAX) N'lax $.k4' AS JSON,  
                array_element varchar(MAX) N'$' AS JSON  
)  
  
```  
  
 **Results**  
  
|k1|k2|col3|col4|col5|array\_element|  
|--------|--------|----------|----------|----------|--------------------|  
|11|null|"text"|null|null|{"k1": 11, "k2": null, "k3": "text"}|  
|1|"text2"|null|"text4"|{ "data": "text4" }|{"k1": true, "k2": "text2", "k4": { "data": "text4" } }|  
|31|"32"|null|null|null|{"k1": 31, "k2": 32 }|  
|41|null|null|0|{ "data": false }|{"k1": 41, "k2": null,       "k4": { "data": false }    }|  
  
## Example \- Load JSON into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table.  
 The following example loads an entire JSON object into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table.  
  
```tsql  
declare @json nvarchar(max) = '{  
 "id" : 2,  
 "firstName": "John",  
 "lastName": "Smith",  
 "isAlive": true,  
 "age": 25,  
 "dateOfBirth": "2015-03-25T12:00:00",  
 "spouse": null  
 }';  
  
 INSERT INTO Person  
 SELECT *   
 FROM OPENJSON(@json)  
 WITH (id int,  
       firstName nvarchar(50), lastName nvarchar(50),   
       isAlive bit, age int,  
       dateOfBirth datetime2, spouse nvarchar(50))  
  
```  
  
## See Also  
 [OPENJSON &#40;Transact-SQL&#41;](../Topic/OPENJSON%20\(Transact-SQL\).md)  
  
  