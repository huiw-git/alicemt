---
title: rxSetComputeContext
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
ms.assetid: 7ad6cde4-c646-46e5-ad0d-2b6c26acbc88
---
# rxSetComputeContext
Defines a new compute context or changes the definition of an existing compute context.

## Usage
`RxComputeContext( computeContext, <other>)`
     
## Arguments
_computeContext_ : A keyword that specifies the type of object to instantiate. For example, possible values are **RxLocalSeq** or **local**, or **RxLocalParallel**. You can also specify a string that references an existing RxComputeContext object.
  
_other_   : Depending on the type of compute context that you are creating, additional parameters might be required.


## Return Value
No change; any existing active compute context remains in effect until the `rxSetComputeContext` function is called to set a new compute context. 


## Remarks
A SQL DDL statement is prepared and passed to the ODBC driver.


## Example

The following example creates a compute context using previously defined variables, sets it as the active compute context to run a function, and then switches back to the local compute context.
~~~~
# switch between local and remote compute contexts
     
     sqlCompute <- RxInSqlServer(connectionstring = sqlConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
     rxSetComputeContext("sqlCompute")
     x <- 1:10
     rxExec(print, x, elemType = "cores", timesToRun = 10)
     rxSetComputeContext("local")

~~~~

For additional examples of how to use local and remote compute contexts, see this tutorial: [Data Science Deep Dive - Using the ScaleR Functions](Data%20Science%20Deep%20Dive:%20Using%20the%20RevoScaleR%20Packages.md)

## See Also
[Comparison of rx Functions and CRAN R Functions](../../Topics\TopicNameNotContainA/Summary-of-rx-Functions.md)

[ScaleR Functions for Working with SQL Server Data](../../Topics\TopicNameNotContainA/ScaleR-Functions-for-Working-with-SQL-Server-Data.md)