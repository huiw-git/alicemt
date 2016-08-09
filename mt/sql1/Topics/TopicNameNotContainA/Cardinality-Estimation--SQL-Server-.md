---
title: "Cardinality Estimation (SQL Server)"
ms.custom: na
ms.date: 2016-05-11
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Cardinality Estimation (SQL Server)
This article illustrates how you can assess and choose the best cardinality estimation (CE) configuration for your SQL system. Most systems benefit from the latest CE because it is the most accurate. Yet in isolated cases it is conceivable that an older CE might lead to a query plan that enables your most important high volume OLTP query to perform better.  
  
 The CE predicts how many rows your query will likely return. The cardinality prediction is used by the query optimizer to generate the optimal query plan. The more accurate the CE, the more optimal the query plan, usually.  
  
## Versions of the CE  
 In 1998, a major update of the CE was part of Microsoft SQL Server 7.0, for which the compatibility level was 70. Subsequent updates came with [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)] and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] 2016, meaning compatibility levels 120 and 130. The CE updates for levels 120 and 130 incorporate assumptions and algorithms that work well on modern data warehousing workloads and on OLTP (online transaction processing).  
  
 **Compatibility level:** You can ensure your database is at a particular level by using the following Transact-SQL code.  
  
```tsql  
SELECT ServerProperty('ProductVersion');  
go  
  
ALTER DATABASE <yourDatabase>  
    SET COMPATIBILITY_LEVEL = 130;  
go  
  
SELECT    d.name, d.compatibility_level  
    FROM  sys.databases AS d  
    WHERE d.name = 'yourDatabase';  
go  
```  
  
 For a SQL Server database set at compatibility level 120, activation of the trace flag 9481 forces the system to use the CE for level 70.  
  
 **Legacy CE:** For a SQL Server database set at compatibility level 130, the level 120 CE can be can be activated by using the following Transact-SQL statement.  
  
```tsql  
ALTER DATABASE <yourDatabase>  
    SCOPED CONFIGURATION  
        LEGACY_CARDINALITY_ESTIMATION = ON;  
go  
  
SELECT  name, value  
    FROM  sys.database_scoped_configurations  
    WHERE name = 'LEGACY_CARDINALITY_ESTIMATION';  
```  
  
 **Query store:**Starting with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] 2016 the query store is a handy tool for examining the performance of your queries.  In SQL Server Management Studio (SSMS.exe), in the **Object Explorer** under your database node, a **Query Store** node is displayed  when the query store is ON.  
  
```tsql  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE = ON;  
go  
  
SELECT  
        q.actual_state_desc    AS [actual_state_desc-ofQueryStore],  
        q.desired_state_desc,  
        q.query_capture_mode_desc  
    FROM  
        sys.database_query_store_options  AS q;  
go  
  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE CLEAR;  
```  
  
 *Tip:* We recommend that each month you install the latest release of [(SSMS.exe)](http://msdn.microsoft.com/library/mt238290.aspx).  
  
 Another option for tracking the cardinality predictions of the CE is to use the extended event named **query_optimizer_estimate_cardinality**.  The following T-SQL code sample runs on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. It writes a .xel file to C:\Temp\ (although you can change the path). When you open the .xel file in SSMS, its detailed information is displayed in a user friendly manner.  
  
```tsql  
DROP EVENT SESSION Test_the_CE_qoec_1 ON SERVER;  
go  
  
CREATE EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    ADD EVENT sqlserver.query_optimizer_estimate_cardinality  
	   (  
        ACTION (sqlserver.sql_text)  
            WHERE (  
                sql_text LIKE '%yourTable%'  
                and sql_text LIKE '%SUM(%'  
            )  
    )  
    ADD TARGET package0.asynchronous_file_target   
        (SET  
            filename = 'c:\temp\xe_qoec_1.xel',  
            metadatafile = 'c:\temp\xe_qoec_1.xem'  
        );  
go  
  
ALTER EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    STATE = START;  --STOP;  
go  
```  
  
 For information about extended events as tailored for Azure SQL Database, see [Extended events in SQL Database](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/).  
  
## Steps to assess the CE version  
 Your OLTP system might have a few SQL queries whose performance is a significant factor in the performance of your overall system. Examples might be:  
  
-   An OLTP query that runs so frequently that multiple instance of it often run concurrently.  
  
-   A SELECT with substantial aggregation that runs during your OLTP business hours.  
  
 Next are steps you can use to assess whether any of your most important queries perform less well under the latest CE. Some of the steps are performed by running a code sample presented in a preceding section.  
  
1.  Open SSMS. Ensure your  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]database is set to the highest available compatibility level.  
  
2.  Perform the following preliminary steps:  
  
    1.  Open SSMS.  
  
    2.  Run the T-SQL to ensure that your  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database is set to the highest available compatibility level.  
  
    3.  Ensure that your database has its LEGACY_CARDINALITY_ESTIMATION configuration turned OFF.  
  
    4.  CLEAR your query store. Of course, ensure your query store is ON.  
  
    5.  Run the statement: \`SET NoCount OFF;`  
  
3.  Run the statement: \`SET STATISTICS XML ON;`  
  
4.  Run your important query.  
  
5.  In the results pane, on the **Messages** tab, note the actual number of rows affected.  
  
6.  In the results pane on the **Results** tab, double-click the cell that contains the statistics in XML format. A graphic query plan is displayed.  
  
7.  Right-click the first box in the graphic query plan, and then click **Properties**.  
  
8.  For later comparison with a different configuration, note the values for the following properties:  
  
    -   **CardinalityEstimationModelVersion**.  
  
    -   **Estimated Number of Rows**.  
  
    -   **Estimated I/O Cost**, and several similar *Estimated* properties that involve actual performance rather than row count predictions.  
  
    -   **Logical Operation** and **Physical Operation**. *Parallelism* is a good value.  
  
    -   **Actual Execution Mode**. *Batch* is a good value, better than *Row*.  
  
9. Compare the estimated number of rows to the actual number of rows. Is the CE inaccurate by 1% (high or low), or by 10%?  
  
10. Run: \`SET STATISTICS XML OFF;`  
  
11. Run the T-SQL to decrease the compatibility level of your database by one level (such as from 130 down to 120).  
  
12. Rerun all the non-preliminary steps.  
  
13. Compare the CE property values from the two runs.      Is the inaccuracy percentage under the newest CE less than under the older CE?  
  
14. Finally, compare the various performance property values from the two runs.  
  
    -   Did you query use a different plan under the two differing CE estimations?  
  
    -   Did you query run slower under the latest CE?  
  
    -   Unless your query runs better and with a different plan under the older CE, you almost certainly want the latest CE.  
  
    -   However, if your query runs with a faster plan under the older CE, consider forcing the system to use the faster plan and to ignore the CE. This way you can have the latest CE on for everything, while keeping the faster plan in the one odd case.  
  
### How to force a particular query plan  
 The query store gives you different ways that you can force the system to use a particular query plan:  
  
-   Execute **sp_query_store_force_plan**.  
  
-   In the SSMS, expand your **Query Store** node, right-click **Top Resource Consuming Nodes**, and then click **View Top Resource Consuming Nodes**. The display shows buttons labeled **Force Plan** and **Unforce Plan**.  
  
 For more information about the query store, see [Monitoring Performance By Using the Query Store](../../Topics/TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md).  
  
## Examples  
 The following examples show some of the changes in the new cardinality estimates. The code for estimating cardinality has been rewritten. The logic is complex and it is not possible to provide an exhaustive list of all changes.  
  
> [!NOTE]  
>  These examples are provided as conceptual information. No action is required on your part to change the way you design databases and queries.  
  
### Example A. New cardinality estimates use an average cardinality for recently added ascending data  
 This example demonstrates how the new cardinality estimator can improve cardinality estimates for ascending data that exceeds the maximum value in the table during the most recent statistics update.  
  
```  
SELECT item, category, amount FROM dbo.Sales AS s WHERE Date = '2013-12-19';  
```  
  
 In this example, new rows are added to the Sales table each day, the query asks for sales that occurred on 12/19/2013, and statistics were last updated on 12/18/2013. The previous cardinality estimator assumes the 12/19/2013 values do not exist since the date exceeds the maximum date and statistics have not been updated to include the 12/19/2013 values. This situation, known as the ascending key problem, will occur if you load data during the day, and then run queries against the data before statistics are updated.  
  
 This behavior has changed. Now, even if statistics have not been updated for the most recent ascending data that is added since the last statistics update, the new cardinality estimator assumes the values exist and uses the average cardinality for each value in the column as the cardinality estimate.  
  
### Example B. New cardinality estimates assume filtered predicates on the same table have some correlation  
 For this example, assume the table Cars as 1000 rows, Make has 200 matches for 'Honda', Model has 50 matches for 'Civic', and that all of the Civics are Hondas. Therefore, 20% of the values in the Make column are 'Honda', 5% of the values in the Model column are 'Civic', and the actual number of Honda Civics is 50. The previous cardinality estimates assume the values in the Make and the Model columns are independent of each other. The previous query optimizer estimates there are 10 Honda Civics (.05 \* .20 \* 1000 rows = 10 rows).  
  
```  
SELECT year, purchase_price FROM dbo.Cars WHERE Make = 'Honda' AND Model = 'Civic';  
```  
  
 This behavior has changed. Now, the new cardinality estimates assume the Make and Model columns have *some* correlation. The query optimizer estimates a higher cardinality by adding an exponential component to the estimation equation. The query optimizer now estimates that 22.36 rows ( .05 * SQRT(.20) \* 1000 rows = 22.36 rows ) match the predicate. For this scenario and specific data distribution, 22.36 rows is closer to the actual 50 rows that the query will return.  
  
 Note, the new cardinality estimator logic sorts the predicate selectivities and increases the exponent. For example, if the predicate selectivities were .05, .20, and .25, the cardinality estimate would be (.05 * SQRT(.20) \* SQRT(SQRT(.25)) ).  
  
### Example C. New cardinality estimates assume filtered predicates on different tables are independent  
 For this example, the previous cardinality estimator assumes that the predicate filters s.type and r.date are correlated. However, test results on modern workloads showed that predicate filters on columns in different tables are usually not correlated with each other.  
  
```  
SELECT s.ticket, s.customer, r.store FROM dbo.Sales AS s CROSS JOIN dbo.Returns AS r  
WHERE s.ticket = r.ticket AND s.type = 'toy' AND r.date = '2013-12-19';  
```  
  
 This behavior has changed. Now, the new cardinality estimator logic assumes that s.type is not correlated with r.date. In practical terms, the assumption is that toys are returned every day and not only on a specific day. In this case, the new cardinality estimates will be a smaller number than the previous cardinality estimates.  
  
## See Also  
 [Monitor and Tune for Performance](../../Topics/TopicNameNotContainA/Monitor-and-Tune-for-Performance.md)