---
title: Validate, Query, and Change JSON Data with Built-in Functions (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
---
# Validate, Query, and Change JSON Data with Built-in Functions (SQL Server)
  The built\-in support for JSON includes the following built\-in functions described in this topic.  
  
-   [ISJSON](#ISJSON) tests whether a string contains valid JSON.  
  
-   [JSON\_VALUE](#VALUE) extracts a scalar value from a JSON string.  
  
-   [JSON\_QUERY](#QUERY) extracts an object or an array from a JSON string.  
  
-   [JSON\_MODIFY](#MODIFY) updates the value of a property in a JSON string and returns the updated JSON string.  
  
##  <a name="ISJSON"></a> Validate JSON text by using the ISJSON function  
 The **ISJSON** function tests whether a string contains valid JSON.  
  
 The following example returns the JSON text if the column contains valid JSON.  
  
```tsql  
SELECT id, json_col  
FROM tab1  
WHERE ISJSON(json_col) > 0  
```  
  
 For more info, see [ISJSON &#40;Transact-SQL&#41;](../Topic/ISJSON%20\(Transact-SQL\).md).  
  
##  <a name="VALUE"></a> Extract a value from JSON text by using the JSON\_VALUE function  
 The **JSON\_VALUE** function extracts a scalar value from a JSON string.  
  
 The following example extracts the value of a JSON property into a local variable.  
  
```tsql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
 For more info, see [JSON_VALUE &#40;Transact-SQL&#41;](../Topic/JSON_VALUE%20\(Transact-SQL\).md).  
  
##  <a name="QUERY"></a> Extract an object or an array from JSON text by using the JSON\_QUERY function  
 The **JSON\_QUERY** function extracts an object or an array from a JSON string.  
  
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
  
 For more info, see [JSON_QUERY &#40;Transact-SQL&#41;](../Topic/JSON_QUERY%20\(Transact-SQL\).md).  
  
##  <a name="JSONCompare"></a> Compare JSON\_VALUE and JSON\_QUERY  
 The key difference between **JSON\_VALUE** and **JSON\_QUERY** is that **JSON\_VALUE** returns a scalar value, while **JSON\_QUERY** returns an object or an array.  
  
 Consider the following sample JSON text.  
  
```json  
{ "a": "[1,2]", "b": [1,2], "c": "hi" }  
```  
  
 In this sample JSON text, data members "a" and "c" are string values, while data member "b" is an array. **JSON\_VALUE** and **JSON\_QUERY** return the following results:  
  
|Query|**JSON\_VALUE** returns|**JSON\_QUERY** returns|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL or error|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|\[1,2\]|NULL or error|  
|**$.b**|NULL or error|\[1,2\]|  
|**$.b\[0\]**|1|NULL or error|  
|**$.c**|hi|NULL or error|  
  
## Test JSON\_VALUE and JSON\_QUERY with the AdventureWorks sample database  
 Test the built\-in functions described in this topic by running the following examples with the AdventureWorks sample database, which contains JSON data. To get the AdventureWorks sample database, [click here](http://www.microsoft.com/en-us/download/details.aspx?id=49502).  
  
 In the following examples, the  Info column in the SalesOrder\_json table contains JSON text.  
  
### Example 1 \- Return both standard columns and JSON data  
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
  
### Example 2\- Aggregate and filter JSON values  
 The following query aggregates subtotals by customer name \(stored in JSON\) and status \(stored in an ordinary column\). Then it filters the results by city \(stored in JSON\), and OrderDate \(stored in an ordinary column\).  
  
```tsql  
SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total  
FROM Sales.SalesOrder_json  
WHERE TerritoryID = @territoryid  
AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city  
AND OrderDate > '1/1/2015'  
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status  
HAVING SUM(SubTotal) > 1000  
  
```  
  
##  <a name="MODIFY"></a> Update property values in JSON text by using the JSON\_MODIFY function  
 The **JSON\_MODIFY**  function updates the value of a property in a JSON string and returns the updated JSON string.  
  
 The following example updates the value of a property in a variable that contains JSON.  
  
```tsql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')  
```  
  
 For more info, see [JSON_MODIFY &#40;Transact-SQL&#41;](../Topic/JSON_MODIFY%20\(Transact-SQL\).md).  
  
## Learn more about built\-in JSON support in SQL Server  
 [Blog posts by Microsoft Program Manager Jovan Popovic](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## See Also  
 [ISJSON &#40;Transact-SQL&#41;](../Topic/ISJSON%20\(Transact-SQL\).md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../Topic/JSON_VALUE%20\(Transact-SQL\).md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../Topic/JSON_QUERY%20\(Transact-SQL\).md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../Topic/JSON_MODIFY%20\(Transact-SQL\).md)   
 [JSON Path Expressions &#40;SQL Server&#41;](../Topic/JSON%20Path%20Expressions%20\(SQL%20Server\).md)  
  
  