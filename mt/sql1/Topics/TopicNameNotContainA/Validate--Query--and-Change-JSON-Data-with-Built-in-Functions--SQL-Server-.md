---
title: "Validate, Query, and Change JSON Data with Built-in Functions (SQL Server)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Validate, Query, and Change JSON Data with Built-in Functions (SQL Server)
The built-in support for JSON includes the following built-in functions described in this topic.  
  
-   [ISJSON](#ISJSON) tests whether a string contains valid JSON.  
  
-   [JSON_VALUE](#VALUE) extracts a scalar value from a JSON string.  
  
-   [JSON_QUERY](#QUERY) extracts an object or an array from a JSON string.  
  
-   [JSON_MODIFY](#MODIFY) updates the value of a property in a JSON string and returns the updated JSON string.  
  
##  <a name="ISJSON"></a> Validate JSON text by using the ISJSON function  
 The **ISJSON** function tests whether a string contains valid JSON.  
  
 The following example returns the JSON text if the column contains valid JSON.  
  
```tsql  
SELECT id, json_col  
FROM tab1  
WHERE ISJSON(json_col) > 0  
```  
  
 For more info, see [ISJSON (Transact-SQL)](assetId:///c836f3d3-3e17-44ae-92bf-f341918896c3).  
  
##  <a name="VALUE"></a> Extract a value from JSON text by using the JSON_VALUE function  
 The **JSON_VALUE** function extracts a scalar value from a JSON string.  
  
 The following example extracts the value of a JSON property into a local variable.  
  
```tsql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
 For more info, see [JSON_VALUE (Transact-SQL)](assetId:///cd016e14-11eb-4eaf-bf05-c7cfcc820a10).  
  
##  <a name="QUERY"></a> Extract an object or an array from JSON text by using the JSON_QUERY function  
 The **JSON_QUERY** function extracts an object or an array from a JSON string.  
  
 Consider the following sample JSON text, which contains a complex element .  
  
```json  
DECLARE @jsonInfo VARCHAR(MAX)  
SET @jsonInfo = N'{  
    "info":{    
      "type":1,  
      "address":{    
        "town":"Bristol",  
        "county":"Avon",  
        "country":"England"  
      },  
      "tags":["Sport", "Water polo"]  
   },  
   "type":"Basic"  
}'  
```  
  
 The following example shows how to return a JSON fragment in query results.  
  
```tsql  
SELECT FirstName, LastName,   
       JSON_QUERY(jsonInfo, '$.info.address') AS Address  
FROM Person.Person  
ORDER BY LastName  
```  
  
 For more info, see [JSON_QUERY (Transact-SQL)](assetId:///1ab0d90f-19b6-4988-ab4f-22fdf28b7c79).  
  
##  <a name="JSONCompare"></a> Compare JSON_VALUE and JSON_QUERY  
 The key difference between **JSON_VALUE** and **JSON_QUERY** is that **JSON_VALUE** returns a scalar value, while **JSON_QUERY** returns an object or an array.  
  
 Consider the following sample JSON text.  
  
```json  
{ "a": "[1,2]", "b": [1,2], "c": "hi" }  
```  
  
 In this sample JSON text, data members "a" and "c" are string values, while data member "b" is an array. **JSON_VALUE** and **JSON_QUERY** return the following results:  
  
|Query|**JSON_VALUE** returns|**JSON_QUERY** returns|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL or error|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL or error|  
|**$.b**|NULL or error|[1,2]|  
|**$.b[0]**|1|NULL or error|  
|**$.c**|hi|NULL or error|  
  
## Test JSON_VALUE and JSON_QUERY with the AdventureWorks sample database  
 Test the built-in functions described in this topic by running the following examples with the AdventureWorks sample database, which contains JSON data. To get the AdventureWorks sample database, [click here](http://www.microsoft.com/en-us/download/details.aspx?id=49502).  
  
 In the following examples, the  Info column in the SalesOrder_json table contains JSON text.  
  
### Example 1 - Return both standard columns and JSON data  
 The following query returns both standard relational columns and values from a JSON column.  
  
```tsql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,  
             JSON_QUERY(Info, '$.ShippingInfo') ShippingInfo,  
             JSON_QUERY(Info, '$.BillingInfo') BillingInfo,  
             JSON_VALUE(Info, '$.SalesPerson.Name') SalesPerson,  
             JSON_VALUE(Info, '$.ShippingInfo.City') City,  
             JSON_VALUE(Info, '$.Customer.Name') Customer,  
             JSON_QUERY(OrderItems, '$') OrderItems  
FROM Sales.SalesOrder_json  
WHERE ISJSON(Info) > 0  
  
```  
  
### Example 2- Aggregate and filter JSON values  
 The following query aggregates subtotals by customer name (stored in JSON) and status (stored in an ordinary column). Then it filters the results by city (stored in JSON), and OrderDate (stored in an ordinary column).  
  
```tsql  
SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total  
FROM Sales.SalesOrder_json  
WHERE TerritoryID = @territoryid  
AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city  
AND OrderDate > '1/1/2015'  
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status  
HAVING SUM(SubTotal) > 1000  
  
```  
  
##  <a name="MODIFY"></a> Update property values in JSON text by using the JSON_MODIFY function  
 The **JSON_MODIFY**  function updates the value of a property in a JSON string and returns the updated JSON string.  
  
 The following example updates the value of a property in a variable that contains JSON.  
  
```tsql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')  
```  
  
 For more info, see [JSON_MODIFY (Transact-SQL)](assetId:///96bc8255-a037-4907-aec4-1a9c30814651).  
  
## Learn more about built-in JSON support in SQL Server  
 [Blog posts by Microsoft Program Manager Jovan Popovic](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## See Also  
 [ISJSON (Transact-SQL)](assetId:///c836f3d3-3e17-44ae-92bf-f341918896c3)   
 [JSON_VALUE (Transact-SQL)](assetId:///cd016e14-11eb-4eaf-bf05-c7cfcc820a10)   
 [JSON_QUERY (Transact-SQL)](assetId:///1ab0d90f-19b6-4988-ab4f-22fdf28b7c79)   
 [JSON_MODIFY (Transact-SQL)](assetId:///96bc8255-a037-4907-aec4-1a9c30814651)   
 [JSON Path Expressions (SQL Server)](../../Topics/TopicNameNotContainA/JSON-Path-Expressions--SQL-Server-.md)