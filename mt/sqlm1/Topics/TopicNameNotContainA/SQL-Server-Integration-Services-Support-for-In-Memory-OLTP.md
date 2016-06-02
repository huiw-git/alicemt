---
title: SQL Server Integration Services Support for In-Memory OLTP
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea82a9b9-e9ed-4d6f-b3fd-917f6c687ae3
---
# SQL Server Integration Services Support for In-Memory OLTP
  You can use a memory\-optimized table, a view referencing memory\-optimized tables, or a natively compiled stored procedure as the source or destination for your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] \(SSIS\) package. You can use [ADO NET Source](../../Topics\TopicNameNotContainA/ADO-NET-Source.md), [OLE DB Source](../../Topics\TopicNameNotContainA/OLE-DB-Source.md), or [ODBC Source](../../Topics\TopicNameNotContainA/ODBC-Source.md) in the data flow of an SSIS package and configure the source component to retrieve data from a memory\-optimized table or a view, or specify a SQL statement to execute a natively compiled stored procedure. Similarly, you can use [ADO NET Destination](../../Topics\TopicNameNotContainA/ADO-NET-Destination.md), [OLE DB Destination](../../Topics\TopicNameNotContainA/OLE-DB-Destination.md), or [ODBC Destination](../../Topics\TopicNameNotContainA/ODBC-Destination.md) to load data into a memory\-optimized table or a view, or specify a SQL statement to execute a natively compiled stored procedure.  
  
 You can configure the above mentioned source and destination components in an SSIS package to read from\/write to memory\-optimized tables and views in the same way as with other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tables and views. However, you need to be aware of the important points in the following section when using natively compiled stored procedures.  
  
## Invoking a natively compiled stored procedure from an SSIS Package  
 To invoke a natively compiled stored procedure from an SSIS package, we recommend that you use an ODBC Source or ODBC Destination with an SQL statement of the format: **\<procedure name\>** without the **EXEC** keyword. If you use the EXEC keyword in the SQL statement, you will see an error message because the ODBC connection manager interprets the SQL command text as a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement rather than a stored procedure and use cursors, which are not supported for execution of natively compiled stored procedures. The connection manager treats the SQL statement without the EXEC keyword as a stored procedure call and will not use a cursor.  
  
 You can also use ADO .NET Source and OLE DB Source to invoke a natively compiled stored procedure, but we recommend that you use ODBC Source. If you configure the ADO .NET Source to execute a natively compiled stored procedure, you will see an error message because the data provider for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(SqlClient\), which the ADO .NET Source uses by default, does not support execution of natively compiled stored procedures. You can configure the ADO .NET Source to use the ODBC Data Provider, OLE DB Provider for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client. However, note that the ODBC Source performs better than ADO .NET Source with ODBC Data Provider.  
  
## See Also  
 [SQL Server Support for In-Memory OLTP](../../Topics\TopicNameNotContainA/SQL-Server-Support-for-In-Memory-OLTP.md)  
  
  