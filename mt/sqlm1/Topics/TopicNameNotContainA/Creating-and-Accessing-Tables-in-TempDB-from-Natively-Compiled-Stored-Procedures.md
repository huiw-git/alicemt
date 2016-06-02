---
title: Creating and Accessing Tables in TempDB from Natively Compiled Stored Procedures
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
---
# Creating and Accessing Tables in TempDB from Natively Compiled Stored Procedures
  Creating and accessing tables in TempDB from natively compiled stored procedures is not supported. Instead, use table types and table variables. The following example shows how the use of a temp table with three columns \(id, ProductID, Quantity\) can be replaced using a table variable **@OrderQuantityByProduct** of type **dbo.OrderQuantityByProduct**:  
  
```tsql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'ENGLISH'  
)  
  -- declare table variables for the list of orders   
  DECLARE @OrderQuantityByProduct dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @OrderQuantityByProduct SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## See Also  
 [Migration Issues for Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md)   
 [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md)  
  
  