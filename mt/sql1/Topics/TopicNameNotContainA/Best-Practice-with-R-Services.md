---
title: "Best Practice with R Services"
ms.custom: na
ms.date: 07/04/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8f1f119-8583-4243-9d30-44237a66288f
caps.latest.revision: 13
---
# Best Practice with R Services
This topic outlines the best practices for using [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] with your workload.  
  
## When to use [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] and when to use R  
 [TBD]  
  
## [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] compute context overhead  
 When using the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] compute context with models smaller than 5-10M rows, you may notice that it takes around 3 seconds to build a model; with the local context it will only take around .4 seconds. However, this overhead remains fixed as the data scales up. At > 10M rows, using the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] compute context will be around 40-50% faster.  
  
## Capacity planning  
 We strongly recommend that you prototype your solution with a non-trivial data set and algorithms to establish a baseline for capacity and performance. In the absence of these, you can use a ballpark of [TBD] cores and [TBD] RAM per user.  
  
## Concurrent jobs  
 How many max? Perf for multiples in parallel?  
  
## Returning predictions  
 When using predictions that contain millions of rows, you may see better performance by writing the prediction data to a table instead of directly returning the information as a query result.  
  
## Parallel processing  
  
> [!NOTE]  
>  Parallel processing  is only supported in Enterprise Edition. You can include the statements and parameters for parallel processing when using Standard Edition, but they will have no effect and the R scripts will be ran in a single process.  
  
 R scripts that execute using the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] compute context can be ran in parallel. This is accomplished by using one of the following methods:  
  
-   The `@parallel = 1` argument when calling `sp_execute_external_script` from [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
-   The  `numTasks` argument when using `RxInSqlServer` from an R client.  
  
 When using `@parallel = 1`,  if the R script can be parallelized, rows will be distributed according to the max degree of parallelism  setting (**MAXDOP**). When using `RxInSqlServer`, you can specify the number of tasks (processes,) to run for each computation by using the `numTasks` argument. Additionally, when using an R client, you can use `rxOptions(numCoresToUse=n)` to control how many cores (actually, threads) are used in parallel within each process. There is a tradeoff between using `numCoresToUse` and `numTasks` that depends upon the specific algorithm, type of data, hardware, and other running jobs.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] may start fewer tasks than specified (or than configured using MAXDOP,) if there is not enough data, too many resources, too many resources are being used by other jobs, or if `numTasks` exceeds MAXDOP.  
  
## Streaming  
  
> [!NOTE]  
>  Streaming  is only supported in Enterprise Edition. You can include the statements and parameters for streaming when using Standard Edition, but they will have no effect.  
  
 Streaming allows R scripts to work with data that doesn't fit in memory. For example, if there are billion rows to score using a predict function, you can specify the number of rows that will be read and sent to the R script at a time. This is accomplished using one of the following methods:  
  
-   The `@r_rowsPerRead` parameter in the `@params` collection when using `sp_execute_external_script` from [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
-   The `rowsPerRead` argument when using `RxSqlServerData` from an R client.  
  
 By using `@r_rowsPerRead` or `rowsPerRead`, you can control the number of rows being read at one time. This might be useful to mitigate server performance issues if, for example, a large model is being trained. Note that setting the number of rows read can only be used in cases where the output of the R script does not depend on reading or looking at the entire set of rows.  
  
 Setting the number of rows to read should be considered a hint. For the hint to be applied, it must be possible to generate a query plan that includes parallel processing.  
  
## Performance monitoring and tuning  
  
### Monitoring R jobs