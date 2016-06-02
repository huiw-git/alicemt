---
title: Format Query Results as JSON with FOR JSON (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
---
# Format Query Results as JSON with FOR JSON (SQL Server)
  Export data from SQL Server as JSON, or format query results as JSON,  by adding the **FOR JSON** clause to a **SELECT** statement.  
  
 When you use the **FOR JSON** clause, you can specify the structure of the output explicitly, or let the structure of the SELECT statement determine the output.  
  
-   **Use PATH mode with the FOR JSON clause**. When you use **PATH** mode with the **FOR JSON** clause, you maintain full control over the format of the JSON output. You can create wrapper objects and nest complex properties.  
  
-   **Use AUTO mode with the FOR JSON clause**. When you use **AUTO** mode with the **FOR JSON** clause, the JSON output is formatted automatically based on the structure of the SELECT statement.  
  
 Use the **FOR JSON** clause to delegate the formatting of JSON output from your client applications to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more info, see [Use FOR JSON output in SQL Server and in client apps &#40;SQL Server&#41;](../Topic/Use%20FOR%20JSON%20output%20in%20SQL%20Server%20and%20in%20client%20apps%20\(SQL%20Server\).md).  
  
 ![FOR JSON](../../Images\Image\ImageNotContaina/JSONSlides2FORJSON.png "JSONSlides2FORJSON")  
  
## Use PATH mode with the FOR JSON clause  
 Here's an example that uses **PATH** mode with the **FOR JSON** clause. For more info and examples, see [Format Nested JSON Output with PATH Mode &#40;SQL Server&#41;](../Topic/Format%20Nested%20JSON%20Output%20with%20PATH%20Mode%20\(SQL%20Server\).md). For syntax and usage, see [FOR Clause &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md).  
  
 In **PATH** mode, you can use the dot syntax – for example, `'Item.Price'` – to format nested output. This example also uses the **ROOT** option to specify a named root element.  
  
 ![Diagram of flow of FOR JSON output](../../Images\Image\ImageNotContaina/FORJSON_example1.png "FORJSON_example1")  
  
## Use AUTO mode with the FOR JSON clause  
 Here's a sample query that uses **AUTO** mode with the **FOR JSON** clause. For more info and examples, see [Format JSON Output Automatically with AUTO Mode &#40;SQL Server&#41;](../Topic/Format%20JSON%20Output%20Automatically%20with%20AUTO%20Mode%20\(SQL%20Server\).md). For syntax and usage, see [FOR Clause &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md).  
  
 In **AUTO** mode, the structure of the SELECT statement determines the format of the JSON output. By default, **null** values are not included in the output. You can use the **INCLUDE\_NULL\_VALUES** to change this behavior.  
  
 **Query:**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **Result**  
  
```json  
[   
   { "name": "John" },  
   { "name": "Jane", "surname": "Doe" }  
]  
  
```  
  
## Control the JSON output with options with the FOR JSON clause  
 Control the output of the **FOR JSON** clause by using the following options.  
  
 [Add a Root Node to JSON Output with the ROOT Option &#40;SQL Server&#41;](../Topic/Add%20a%20Root%20Node%20to%20JSON%20Output%20with%20the%20ROOT%20Option%20\(SQL%20Server\).md)  
 To add a single, top\-level element to the JSON output, specify the **ROOT** option. If you don't specify the **ROOT** option, the JSON output doesn't have a root element.  
  
 [Include Null Values in JSON Output with the INCLUDE_NULL_VALUES Option &#40;SQL Server&#41;](../Topic/Include%20Null%20Values%20in%20JSON%20Output%20with%20the%20INCLUDE_NULL_VALUES%20Option%20\(SQL%20Server\).md)  
 To include null values in the JSON output, specify the **INCLUDE\_NULL\_VALUES** option. If you don't specify this option, the output does not include JSON properties for NULL values in the query results.  
  
 [Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option &#40;SQL Server&#41;](../Topic/Remove%20Square%20Brackets%20from%20JSON%20Output%20with%20the%20WITHOUT_ARRAY_WRAPPER%20Option%20\(SQL%20Server\).md)  
 To remove the square brackets that surround the JSON output of the **FOR JSON** clause by default, specify the **WITHOUT\_ARRAY\_WRAPPER** option. Use this option to generate a single JSON object as output. If you don't specify this option, the JSON output is enclosed within square brackets.  
  
 For more info about what you see in the output of the **FOR JSON** clause, see the following topics in this section.  
  
 [How FOR JSON converts SQL Server data types to JSON data types &#40;SQL Server&#41;](../Topic/How%20FOR%20JSON%20converts%20SQL%20Server%20data%20types%20to%20JSON%20data%20types%20\(SQL%20Server\).md)  
 The **FOR JSON** clause uses the rules described in this topic to convert SQL data types to JSON types in the JSON output.  
  
 [How FOR JSON escapes special characters and control characters &#40;SQL Server&#41;](../Topic/How%20FOR%20JSON%20escapes%20special%20characters%20and%20control%20characters%20\(SQL%20Server\).md)  
 The **FOR JSON** clause escapes special characters and represents control characters in the JSON output as described in this topic.  
  
## Output of the FOR JSON clause  
 The output of the **FOR JSON** clause has the following characteristics.  
  
1.  The result set contains a single column. A small result set may contain a single row. A large result set contains multiple rows.  
  
     ![Example of FOR JSON output](../../Images\Image\ImageNotContaina/FORJSON_example2.png "FORJSON_example2")  
  
2.  The results are formatted as an array of JSON objects.  
  
    -   The number of elements in the array is equal to the number of rows in the results.  
  
    -   Each row in the result set becomes a separate JSON object in the array.  
  
    -   Each column in the result set becomes a property of the JSON object.  
  
3.  Both the names of columns and their values are escaped according to JSON syntax.  
  
 Here's an example that demonstrates the formatting of the JSON output.  
  
 **Query results**  
  
|||||  
|-|-|-|-|  
|**A**|**B**|**C**|**D**|  
|10|11|12|X|  
|20|21|22|Y|  
|30|31|32|Z|  
  
 **JSON output**  
  
```json  
[  
  { "A":10, "B":11, "C":12, "D":"X" },  
  { "A":20, "B":21, "C":22, "D":"Y" },  
  { "A":30, "B":31, "C":32, "D":"Z" }  
]  
```  
  
## Learn more about FOR JSON and built\-in JSON support in SQL Server  
 [Blog posts by Microsoft Program Manager Jovan Popovic](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## See Also  
 [FOR Clause &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)   
 [Use FOR JSON output in SQL Server and in client apps &#40;SQL Server&#41;](../Topic/Use%20FOR%20JSON%20output%20in%20SQL%20Server%20and%20in%20client%20apps%20\(SQL%20Server\).md)  
  
  