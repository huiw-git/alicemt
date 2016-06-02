---
title: rxSqlServerTableExists
ms.custom: na
ms.devlang: 
  - R
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 251de2a9-ca23-4c17-8e2f-1d8fd27c49cd
---
# rxSqlServerTableExists
Returns a Boolean that indicates whether the specified database table exists.

## Usage

`rxSqlServerTableExists(table, connectionString)`

## Arguments

_table_: A string containing a table name or the name of an `RxSqlServerData` data source that specifies a table.

_connectionString_: A string containing connection information.  If NULL, the connection string from the currently active compute context will be used.

## Remarks
A SQL query is prepared and passed to the ODBC driver.

## Return Value
TRUE if the table exists, FALSE if the table does not exists or was not found.

## Example

The following example checks for the existence of a table and drops it if it exists.
~~~~
if (rxSqlServerTableExists(tempTable)) rxSqlServerDropTable(tempTable)
~~~~

## See Also
[Comparison of rx Functions and CRAN R Functions](../../Topics\TopicNameNotContainA/Summary-of-rx-Functions.md)

[ScaleR Functions for Working with SQL Server Data](../../Topics\TopicNameNotContainA/ScaleR-Functions-for-Working-with-SQL-Server-Data.md)