---
title: Use Nested FOR XML Queries in ASP.NET
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 691ac7dd-afc5-4760-932c-2b1dcd9394ed
---
# Use Nested FOR XML Queries in ASP.NET
  In this example, an ASP.NET application returns XML to a browser by executing a stored procedure in SQL Server. The stored procedure generates XML using nested queries. A similar SELECT statement is shown in the topic [Generating Siblings by Using a Nested AUTO Mode Query](../../Topics\TopicNameContainA/Generate-Siblings-with-a-Nested-AUTO-Mode-Query.md). This example demonstrates one way to use nested FOR XML queries to generate element\-centric XML in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## Example  
  
```  
CREATE PROC GetSalesOrderInfo AS  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
      FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
      for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE, ELEMENTS)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
GO  
```  
  
 This is the .aspx application. It executes the stored procedure and returns XML in the browser:  
  
```  
<%@LANGUAGE=C# Debug=true %>  
<%@import Namespace="System.Xml"%>  
<%@import namespace="System.Data.SqlClient" %><%  
Response.Expires = -1;  
Response.ContentType = "text/xml";  
%>  
  
<%  
using(System.Data.SqlClient.SqlConnection c = new System.Data.SqlClient.SqlConnection("Data Source=server;Database=AdventureWorks;Integrated Security=SSPI;"))  
using(System.Data.SqlClient.SqlCommand cmd = c.CreateCommand())  
{  
   cmd.CommandText = "GetSalesOrderInfo";  
   cmd.CommandType = CommandType.StoredProcedure;  
   cmd.Connection.Open();  
   System.Xml.XmlReader r = cmd.ExecuteXmlReader();  
   System.Xml.XmlTextWriter w = new System.Xml.XmlTextWriter(Response.Output);  
   w.WriteStartElement("Root");  
   r.MoveToContent();  
   while(! r.EOF)  
   {  
      w.WriteNode(r, true);  
   }  
   w.WriteEndElement();  
   w.Flush();  
}  
%>  
```  
  
##### To test the application  
  
1.  Create the stored procedure in the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database.  
  
2.  Save the .aspx application in the c:\\inetpub\\wwwroot directory \(GetSalesOrderInfo.aspx\).  
  
3.  Execute the application \(http:\/\/server\/GetSalesOrderInfo.aspx\).  
  
## See Also  
 [Use Nested FOR XML Queries](../../Topics\TopicNameNotContainA/Use-Nested-FOR-XML-Queries.md)  
  
  