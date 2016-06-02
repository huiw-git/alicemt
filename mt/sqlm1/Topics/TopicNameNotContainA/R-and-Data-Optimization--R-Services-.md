---
title: R and Data Optimization (R Services)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6104878-ed19-47a7-ac37-21e4d6e2a1af
---
# R and Data Optimization (R Services)
## Compute Context

[!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] can use either the __local__ or __SQL__ compute context when performing analysis. When using the __local__ compute context, analysis is performed on the client machine and data must be fetched from [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] over the network. The performance hit incurred for this network transfer depends on the size of the data transferred, speed of the network, and other network transfers occurring at the same time.

If the compute context is __SQL Server__, then the analytic functions are executed inside [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)]. The data is local to the analysis task, so no network overhead is introduced. 

When working with large data sets, you should always use the SQL compute context.

## Table compression

IO performance can often be improved by using either compression or columnar tables (columnar tables inherently use compression.) Generally, data is often repeated in several columns within a table, so using a columnar store takes advantage of these repetitions when compressing the data.

A columnar table may not be as efficient if there are a lot of insertions into the table, but is a good choice if the data is static or only changes infrequently. If a columnar store is not appropriate, enabling compression on a row major table can be used to improve IO.

For more information, see the following documents:

* [Data Compression](../../Topics\TopicNameNotContainA/Data-Compression.md)

* [Enable Compression on a Table or Index](../../Topics\TopicNameContainA/Enable-Compression-on-a-Table-or-Index.md)

## Factors

The R language converts strings from tables into factors. Many data source objects take `colInfo` as a parameter to control how the columns are treated. For example, `c(“fruit” = c(type = “factor”, levels=as.character(c(1:3)), newLevels=c(“apple”, “orange”, “banana”)))` will consume integers 1, 2, and 3 from a table and treat them as factors with levels `apple`, `orange`, and `banana`. 

Data scientists often use factor variables in their formula; however, using factors when the source data is an integer will incur a performance hit as integers are converted to strings at run time. If the table column contains strings instead, we can specify the levels using `colInfo` ahead of time as well. For example, `c(“fruit” = c(type = “factor”, levels= c(“apple”, “orange”, “banana”)))`. This will treat the strings as factors as they are read. 

To avoid run time conversions, consider storing levels as integers in the table and consuming them as they are in the formula. If there is no semantic difference in the model generation, then this approach can lead to better performance.

## Data transformation

Data scientists often use transformation functions written in R as part of the analytics computation. The transformation functions must be applied to each row retrieved from the table during the computation. In [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], this transformation happens in batch mode and involves communication between the R interpreter and the analytics engine. To perform the transformation, the data moves from SQL to the analytics engine and then to the R interpreter process and back, so using transformations can adversely affect the performance of the algorithm significantly depending on the amount of data involved.

It is more efficient to have all necessarily columns in the table, or a view, before performing analysis, as this avoids transformations during the computation. If it is not possible to add additional columns to existing tables, consider creating another table or view with the transformed columns and use an appropriate query the retrieve the data.

## Batching

The SQL data source (`RxSqlServerData`) has an option to indicate the batch size (number of rows to process at a time) using the parameter `rowsPerRead`. At run time, algorithms will read the specified numbered of rows at a time. By default, the value of this parameter is set 50,000 to ensure that the algorithms can perform well even on machines with low memory. If the machine has enough available memory, increasing this value to 500,000 or even a million can yield better performance, especially for large tables. 

Increasing this value may not always produce better results and may require some experimentation to determine the optimal value. The benefits of this will be more evident on a large data set with multiple processes (`numTasks` set to a value greater than `1`).

## Parallel processing

To improve the performance of running rx analytic functions inside [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)], [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] relies on parallel processing using the available cores on the [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] machine. There are two ways to achieve parallelization with [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]:

* When using the `sp_execute_external_script` stored procedure to run an R script, set the `@parallel` parameter to `1`. This is useful for R scripts that do not use RevoScaleR functions (rx functions.) If the script uses RevoScaleR functions, parallel processing is handled automatically and you should not set `@parallel` to `1`.

    If the R script can be parallelized, and if the [!INCLUDE[tsql_md](../../Token\Other/tsql_md.md)] query can be parallelized, then [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] will create multiple parallel processes (up to the __max degree of parallelism MAXDOP__ setting for [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)],) and run the same script across all processes. Each process only receives a portion of the data, so this is not useful with scripts that must see all the data. For example, training a model. However, it is useful when performing tasks such as batch prediction in parallel. For more information on using parallelism with sp\_execute\_external\_script, see the __Advanced tips: parallel processing__ section of [Using R Code in Transact-SQL](Using%20R%20Code%20in%20Transact-SQL%20\(SQL%20Server%20R%20Services\).md).

* When using rx functions with the SQL Compute context, set `numTasks` to the number of processes you wish to create. The actual number of processes created is determined by [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)], and may be less than you requested. The number of processes created can never be more than __MAXDOP__.

    If the R script can be parallelized, and if the [!INCLUDE[tsql_md](../../Token\Other/tsql_md.md)] query can be parallelized, then [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] will create multiple parallel processes when running the rx functions.

The number of processes that will be created depends on a variety of factors such as resource governance, current usage of resources, other sessions, and the query execution plan for the query used with the R script. 

### Query parallelization

To ensure that the data can be analyzed in parallel, the query used to retrieve the data should be framed in such a way that it can render itself for parallel execution. 

[!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] supports working with SQL data sources using `RxSqlServerData` to specify the source. The source can be either a table or a query. For example, `RxSqlServerData(table=”airline”, connectionString = sqlConnString)` or `RxSqlServerData(sqlquery=”select [ArrDelay],[CRSDepTime],[DayOfWeek] from airlineWithIndex where rowNum <= 100000”, connectionString = sqlConnString)`.  As the analytics algorithms pull large volumes of data from the tables, it is important to ensure that the query given to `RxSqlServerData` is optimized for parallel execution. A query that does not result in a parallel execution plan can result in a single process for computation.

[!INCLUDE[ssManStudioFull_md](../../Token\Other/ssManStudioFull_md.md)] can be used to analyze the execution plan, and improve the performance of the query. For example, a missing index on a table can affect the time taken to execute a query. See [Monitor and Tune for Performance](../../Topics\TopicNameNotContainA/Monitor-and-Tune-for-Performance.md) for more information.

Another oversight that can affect the performance is when the query retrieves more columns than are required. For example, if a formula is based on only 3 columns, and the table has 30 columns, do not use a query such as `select *` or one that selects more columns than needed.

> [!NOTE]
> If a table is specified in the data source instead of a query, [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] will internally determine the necessary columns to fetch from the table; however, this approach is unlikely to result in parallel execution.

## Algorithm parameters

Many rx training algorithms support parameters to control how the training model is generated, which can be modified to increase the speed of computation. While the accuracy and correctness of the model is important, the performance of the algorithm may be equally important. It may be possible to improve the performance without reducing the accuracy or correctness in some cases. For example, `rxDTree` supports the `maxDepth` parameter that controls the maximum tree depth. As `maxDepth` is increased, performance can degrade, so it is important to analyze the benefits of increasing the depth vs. the performance impact. 

One of the parameters that can be used with `rxLinMod` and `rxLogit` is the `cube` argument. This argument can be used when the first dependent variable of the formula is a factor variable. If `cube` is set to `TRUE`, the regression is done using a partitioned inverse, it may be faster and use less memory than standard regression computation. If the formula has a large number of variables, the performance gain can be significant.

The RevoScaleR users guide has some useful information for controlling the model fit for various algorithms. For example, with `rxDTree` you can control the balance between time complexity and prediction accuracy by adjusting parameters such as `maxNumBins`, `maxDepth`, `maxComplete`, and `maxSurrogate`. Increasing the depth to beyond 10 or 15 can make the computation very expensive.

For more information on tuning performance for `rxDForest` and `rxDTree`, see [Performance tuning options for rxDForest/rxDTree](https://support.microsoft.com/kb/3104235).

## Model and prediction

Once the training has completed and the best model selected, we recommend storing the model in the database so that it is readily available for predictions. For on-line transaction processing that requires prediction, loading the pre-computed model from the database for the prediction is very efficient. The sample scripts use this approach to serialize and store the model in a database table. For prediction, the model is de-serialized from the database.

Some models generated by algorithms such as lm or glm can be quite large, especially when used on a large data set. There are size limitations to the data that can be stored in [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)]. You should clean up the model before storing it to the database.

> [!NOTE] If fast prediction using a stored model and integrating the analytics into an application is an important scenario, we recommend __DeployR__. It can be used to easily integrate R analytics inside web, desktop, mobile, and dashboard applications. In particular, it is well suited for storing a model and then performing single row prediction using the stored model. For more information, see [About DeployR](https://msdn.microsoft.com/microsoft-r/rserver/deployr-about).

## Resource governance

[!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] supports resource governance for controlling the various resources used by [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]. For example, the default value for memory consumption by R is limited to 20% of the total memory available for [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)]. This is done to ensure that [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] workflows are not severely affected by long running R jobs. However, these limits can be changed by the database administrator. 

The resources limited are __MAX\_CPU\_PERCENT__, __MAX\_MEMORY\_PERCENT__, and __MAX\_PROCESSES__. The [!INCLUDE[tsql_md](../../Token\Other/tsql_md.md)] statement `select * from sys.resource_governor_external_resource_pools` can be used to view the current settings. If [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] is primarily used for R services, then it might be helpful to increase MAX\_CPU\_PERCENT to 40% or 60%. If there many R sessions using the same [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] at the same time, all three will should be increased. To change a value, the [!INCLUDE[tsql_md](../../Token\Other/tsql_md.md)] statement can be used. For example, `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)` sets the memory usage to 40%. The following is an example of setting all three at once: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`. 

> [!NOTE]
> To make changes to these settings take effect immediately, use `ALTER RESOURCE GOVERNOR RECONFIGURE` command after changing a memory, CPU, or max process setting. 

For more information, see [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md).