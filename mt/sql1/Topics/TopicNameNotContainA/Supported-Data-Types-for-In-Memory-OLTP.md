---
title: "Supported Data Types for In-Memory OLTP"
ms.custom: na
ms.date: 2016-05-27
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Supported Data Types for In-Memory OLTP
This article lists the data types that are unsupported for the In-Memory OLTP features of:  
  
-   Memory-optimized tables  
  
-   Natively compiled stored procedures  
  
## Unsupported Data Types  
 The following data types are not supported:  
  
||||  
|-|-|-|  
|[DATETIMEOFFSET](assetId:///a0455b71-ca25-476e-a7a8-0770f1860bb7)|[GEOGRAPHY](assetId:///d9e4952a-1841-4465-a64b-11e9288dba1d)|[GEOMETRY](assetId:///3fefdf7b-f931-404c-821c-82c0375eaf51)|  
|[HIERARCHYID](assetId:///69b756e0-a1df-45b3-8a24-6ded8658aefe)|[ROWVERSION](assetId:///65c9cf0e-3e8a-45f8-87b3-3460d96afb0b)|[XML](assetId:///9198f671-8e61-4ca4-9c3a-859f84020e62)|  
|[sql_variant (Transact-SQL)](assetId:///01229779-8bc1-4c7d-890a-8246d4899250)|User-Defined Types|.|  
  
## Notable Supported Data Types  
 Most data types are supported by the features of In-Memory OLTP. The following few are worth noting explicitly:  
  
|String and Binary Types|For more information|  
|-----------------------------|--------------------------|  
|binary and varbinary*|[binary and varbinary (Transact-SQL)](assetId:///bcce65f9-10db-4b3e-bfaf-dfc06c6f820f)|  
|char and varchar*|[char and varchar (Transact-SQL)](assetId:///282cd982-f4fb-4b22-b2df-9e8478f13f6a)|  
|nchar and nvarchar*|[nchar and nvarchar (Transact-SQL)](assetId:///81ee5637-ee31-4c4d-96d0-56c26a742354)|  
  
 \* For the preceding string and binary data types, starting with SQL Server 2016:  
  
-   An individual memory-optimized table can also have several long columns such as `nvarchar(5000)`, even though their lengths would add to more than the physical row size of 8060 bytes.  
  
-   A memory-optimized table can have max length string and binary columns of data types such as `varchar(max)`.  
  
|Other Types|For more information|  
|-----------------|--------------------------|  
|table types|[Memory-Optimized Table Variables](../../Topics/TopicNameNotContainA/Memory-Optimized-Table-Variables.md)|  
  
## See Also  
 [Transact-SQL Support for In-Memory OLTP](../../Topics/TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md)   
 [Implementing LOB Columns in a Memory-Optimized Table](assetId:///bd8df0a5-12b9-4f4c-887c-2fb78dd79f4e)   
 [Implementing SQL_VARIANT in a Memory-Optimized Table](../../Topics/TopicNameContainA/Implementing-SQL_VARIANT-in-a-Memory-Optimized-Table.md)