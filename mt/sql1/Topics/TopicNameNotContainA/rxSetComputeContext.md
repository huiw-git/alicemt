---
title: "rxSetComputeContext"
ms.custom: na
ms.date: 2016-05-31
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
caps.latest.revision: 6
manager: paulettm
---
# rxSetComputeContext
Sets the active compute context for RevoScaleR computations.

## Usage
`RxSetComputeContext( computeContext, <other>)`
     
## Arguments
_computeContext_ : A keyword that specifies the type of object to instantiate. For example, possible values are **RxLocalSeq** or **local**, or **RxLocalParallel**. You can also specify a string that references an existing RxComputeContext object.
  
_other_   : Depending on the type of compute context that you are creating, additional parameters might be required.


## Return Value
Returns the previously active compute context invisibly. 


## Remarks
If you define a new compute context, it is not used until the `rxSetComputeContext` function is called to set the active compute context.


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
[Comparison of rx Functions and CRAN R Functions](../../Topics/TopicNameNotContainA/Summary-of-rx-Functions.md)

[ScaleR Functions for Working with SQL Server Data](../../Topics/TopicNameNotContainA/ScaleR-Functions-for-Working-with-SQL-Server-Data.md)