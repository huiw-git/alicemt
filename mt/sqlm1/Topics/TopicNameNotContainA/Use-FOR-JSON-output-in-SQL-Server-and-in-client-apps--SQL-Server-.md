---
title: Use FOR JSON output in SQL Server and in client apps (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-json
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 302e5397-b499-4ea3-9a7f-c24ccad698eb
---
# Use FOR JSON output in SQL Server and in client apps (SQL Server)
  The following examples demonstrate some of the ways to use the **FOR JSON** clause or its output in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or in client apps.  
  
## Use FOR JSON output in SQL Server variables  
 The output of the FOR JSON clause is of type NVARCHAR\(MAX\), so it can be assigned to any variable, as shown in the following example.  
  
```tsql  
DECLARE @x NVARCHAR(MAX) = (SELECT TOP 10 * FROM Sales.SalesOrderHeader FOR JSON AUTO)  
```  
  
## Use FOR JSON output in SQL Server user\-defined functions  
 You can create user\-defined functions that format result sets as JSON and return this JSON output. The following example creates a user\-defined function that fetches some sales order detail rows and formats them as a JSON array.  
  
```tsql  
CREATE FUNCTION GetSalesOrderDetails(@salesOrderId int)  
RETURNS NVARCHAR(MAX)  
AS  
BEGIN  
  RETURN (SELECT UnitPrice, OrderQty  
          FROM Sales.SalesOrderDetail  
          WHERE SalesOrderID = @salesOrderId  
          FOR JSON AUTO)  
END  
```  
  
 You can use this function in a batch or query, as shown in the following example.  
  
```tsql  
DECLARE @x NVARCHAR(MAX) = dbo.GetSalesOrderDetails(43659)  
PRINT dbo.GetSalesOrderDetails(43659)  
SELECT TOP 10 H.*, dbo.GetSalesOrderDetails(H.SalesOrderId) AS Details  
FROM Sales.SalesOrderHeader H  
```  
  
## Merge parent and child data into a single table  
 In the following example, each set of child rows is formatted as a JSON array and becomes the value of the Details column in the parent table.  
  
```tsql  
select top 10 SalesOrderId, OrderDate,  
     (select top 3 UnitPrice, OrderQty  
        from Sales.SalesOrderDetail D  
        where H.SalesOrderId = D.SalesOrderID  
        for json auto) as Details  
into SalesOrder  
from Sales.SalesOrderHeader H  
```  
  
## Update the data in JSON columns  
 The following example demonstrates that you can update the value of columns that contain JSON text.  
  
```tsql  
UPDATE SalesOrder  
SET Details =  
    (SELECT TOP 1 UnitPrice, OrderQty  
      FROM Sales.SalesOrderDetail D  
      WHERE D.SalesOrderId = SalesOrder.SalesOrderId  
     FOR JSON AUTO)  
```  
  
## Use FOR JSON output in a C\# client app  
 The following example shows how to retrieve the JSON output of a query into a StringBuilder object in a C\# client app. Assume that the variable queryWithForJson contains the text of a SELECT statement with a FOR JSON clause.  
  
```c#  
var cmd = new SqlCommand(queryWithForJson, conn);  
conn.Open();  
var jsonResult = new StringBuilder();  
var reader = cmd.ExecuteReader();  
if (!reader.HasRows)  
{  
    jsonResult.Append("[]");  
}  
else  
{  
    while (reader.Read())  
    {  
        jsonResult.Append(reader.GetValue(0).ToString());  
    }  
}  
```  
  
## See Also  
 [Format Query Results as JSON with FOR JSON &#40;SQL Server&#41;](../Topic/Format%20Query%20Results%20as%20JSON%20with%20FOR%20JSON%20\(SQL%20Server\).md)  
  
  