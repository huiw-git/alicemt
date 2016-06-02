---
title: Convert JSON Data to Rows and Columns with OPENJSON (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c139901-01e2-49ef-9d62-57e08e32c68e
---
# Convert JSON Data to Rows and Columns with OPENJSON (SQL Server)
  **OPENJSON** rowset function enables you convert JSON text into a set of rows and columns. You can use **OPENJSON** to run SQL queries on JSON collections or to import JSON text into SQL Server tables.  
  
> [!NOTE]  
>  The **OPENJSON** function is available only under **compatibility level 130**. If your database compatibility level is lower than 130, SQL Server will not be able to find and execute **OPENJSON** function. Other JSON functions are available at all compatibility levels. You can check compatibility level in sys.databases view or in database properties.  
>     You can change a compatibility level of database using the following command:   
> ALTER DATABASE DatabaseName SET COMPATIBILITY\_LEVEL \= 130  
  
 **OPENJSON** function will take a single JSON object or collection of JSON objects and transform them into one or multiple rows. By default, **OPENJSON** function will return all key:value pairs that can be found in the first level of JSON object, or all elements in JSON arrays with their indexes.  
  
 You can specify schema of rows that will be returned by **OPENJSON** function using WITH clause. This explicit schema defines the structure of the output.  
  
-   **Use OPENJSON without the result schema**. When you use **OPENJSON** function without specified schema of returned results \(i.e. no WITH clause after OPENJSON\), the function returns a table with three columns \- name of property in the input object \(or index of element in input array\), value of property or array element, and type \(e.g. string, number, boolean, array or object\). Properties of JSON object \(or elements of array\) are returned in separate rows.  
  
     Here's a quick example that uses **OPENJSON**  with the default schema and returns one row for each property of  the JSON object.  
  
    ```tsql  
  
    SET @json = '{"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}';  
  
    SELECT *  
    FROM OPENJSON(@json);  
  
    ```  
  
     **Results**  
  
    |key|value|type|  
    |---------|-----------|----------|  
    |name|John|1|  
    |surname|Doe|1|  
    |age|45|2|  
    |skills|\["SQL","C\#","MVC"\]|4|  
  
     For more info and examples, see [Use OPENJSON with the Default Schema &#40;SQL Server&#41;](../Topic/Use%20OPENJSON%20with%20the%20Default%20Schema%20\(SQL%20Server\).md). For syntax and usage, see [OPENJSON &#40;Transact-SQL&#41;](../Topic/OPENJSON%20\(Transact-SQL\).md).  
  
-   **Use OPENJSON with an explicit schema**. When you specify schema of returned results in WITH clause of **OPENJSON** function, the function returns a table with the columns that you define in the WITH clause. In the WITH clause, you can specify a set output columns, their types, and the paths of the JSON source properties for each output value. **OPENJSON** will iterate through the array of JSON objects, read value on the specified path for each column, and convert value to specified type.  
  
 Here's a quick example that uses **OPENJSON**  with an explicitly specified schema.  
  
```tsql  
SET @json =   
 N'[  
      {  
        "Order": {  
          "Number":"SO43659",  
          "Date":"2011-05-31T00:00:00"  
        },  
        "AccountNumber":"AW29825",  
        "Item": {  
          "Price":2024.9940,  
          "Quantity":1  
        }  
      },  
      {  
        "Order": {  
          "Number":"SO43661",  
          "Date":"2011-06-01T00:00:00"  
        },  
        "AccountNumber":"AW73565",  
        "Item": {  
          "Price":2024.9940,  
          "Quantity":3  
        }  
     }  
]'  
  
SELECT * FROM  
OPENJSON ( @json )  
WITH (   
             Number   varchar(200) '$.Order.Number' ,  
             Date     datetime     '$.Order.Date',  
             Customer varchar(200) '$.AccountNumber',  
             Quantity int          '$.Item.Quantity'  
)  
```  
  
 **Results**  
  
|Number|Date|Customer|Quantity|  
|------------|----------|--------------|--------------|  
|SO43659|2011\-05\-31T00:00:00|AW29825|1|  
|SO43661|2011\-06\-01T00:00:00|AW73565|3|  
  
 This function returns and formats the elements of a JSON array.  
  
-   For each element in the JSON array, **OPENJSON** generates a new row in the output table. Two elements in JSON array are converted into two rows in returned table.  
  
-   For each column, specified by using the `colName type json_path` syntax, **OPENJSON** function converts the value found in array elements on the specified path, converts them to specified type, and populates a cell in the output table. In this example, values for Date column are taken from each object on a path `$.Order.Date` and converted to datetime values.  
  
     Once you transform JSON collection to a rowset, you can run any SQL query on returned data or insert it into a table. For more info and examples, see [Use OPENJSON with an Explicit Schema &#40;SQL Server&#41;](../Topic/Use%20OPENJSON%20with%20an%20Explicit%20Schema%20\(SQL%20Server\).md). For syntax and usage, see [OPENJSON &#40;Transact-SQL&#41;](../Topic/OPENJSON%20\(Transact-SQL\).md).  
  
## Learn more about OPENJSON and built\-in JSON support in SQL Server  
 [Blog posts by Microsoft Program Manager Jovan Popovic](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## See Also  
 [OPENJSON &#40;Transact-SQL&#41;](../Topic/OPENJSON%20\(Transact-SQL\).md)  
  
  