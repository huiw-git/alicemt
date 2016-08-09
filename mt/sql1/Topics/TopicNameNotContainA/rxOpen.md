---
title: "rxOpen"
ms.custom: na
ms.date: 2016-05-30
ms.devlang: 
  - R
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15b71322-ce2f-4825-8c69-7b21b8097b88
caps.latest.revision: 5
manager: paulettm
---
# rxOpen
Opens an existing ScaleR data source object.

## Usage

`rxOpen(src, mode = "r")`

## Arguments

_src_: An existing RxDataSource object.

_mode_: A string indicating the mode to use when accessing the data source. Currently only **r** is supported, meaning "read-only".

## Remarks
This is one of several generic functions in the  RevoScaleR package that are used for managing data source objects.
For information about how to create a SQL Server data source, see [RxSqlServer](../../Topics/TopicNameNotContainA/RxSqlServerData.md).
For information about working with other data sources such as Hadoop, Teradata, and text files, see the [Microsoft R Server documentation](http://msdn.microsoft.com/microsoft-r/index#) in the MSDN library.

## Return Value
TRUE if the operation was successful; FALSE otherwise. 

## Example
For examples of how to work with ScaleR data sources, see [Data Sources](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-user-guide-3-data-source).

## See Also
[Comparison of rx Functions and CRAN R Functions](../../Topics/TopicNameNotContainA/Summary-of-rx-Functions.md)

[ScaleR Functions for Working with SQL Server Data](../../Topics/TopicNameNotContainA/ScaleR-Functions-for-Working-with-SQL-Server-Data.md)