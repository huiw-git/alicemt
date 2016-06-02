---
title: Monitor and Tune for Performance
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
---
# Monitor and Tune for Performance
  The goal of monitoring databases is to assess how a server is performing. Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.  
  
 Ongoing evaluation of the database performance helps you minimize response times and maximize throughput, yielding optimal performance. Efficient network traffic, disk I\/O, and CPU usage are key to peak performance. You need to thoroughly analyze the application requirements, understand the logical and physical structure of the data, assess database usage, and negotiate tradeoffs between conflicting uses such as online transaction processing \(OLTP\) versus decision support.  
  
## Benefits of Monitoring and Tuning Databases for Performance  
 Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and the Microsoft Windows operating system provide utilities that allow you to view the current condition of the database and to track performance as conditions change. There are a variety of tools and techniques that can be used to monitor [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Understanding how to monitor [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can help you:  
  
-   Determine whether you can improve performance. For example, by monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables are required.  
  
-   Evaluate user activity. For example, by monitoring users trying to connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can determine whether security is set up adequately and test applications or development systems. For example, by monitoring SQL queries as they are executed, you can determine whether they are written correctly and producing the expected results.  
  
-   Troubleshoot any problems or debug application components, such as stored procedures.  
  
### Monitoring in a Dynamic Environment  
 Monitoring is important because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a service in a dynamic environment. Changing conditions result in changing performance. In your evaluations, you can see performance changes as the number of users increases, user access and connection methods change, database contents grow, client applications change, data in the applications changes, queries become more complex, and network traffic rises. By using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools to monitor performance, you can associate some changes in performance with changing conditions and complex queries. The following scenarios provide examples:  
  
-   By monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables where the queries execute are required.  
  
-   By monitoring [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries as they are executed, you can determine whether the queries are written correctly and producing the expected results.  
  
-   By monitoring users that try to connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can determine whether security is set up adequately and test applications or development systems.  
  
 Response time is the length of time required for the first row of the result set to be returned to the user in the form of visual confirmation that a query is being processed. Throughput is the total number of queries handled by the server during a specified period of time.  
  
 As the number of users increases, so does the competition for a server's resources, which in turn increases response time and decreases overall throughput.  
  
## Monitoring and Tuning Performance Tasks  
  
|Topic|Task Description|  
|-----------|----------------------|  
|[Monitor SQL Server Components](../../Topics\TopicNameNotContainA/Monitor-SQL-Server-Components.md)|Provides the necessary steps required to effectively monitor any component of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[Performance Monitoring and Tuning Tools](../../Topics\TopicNameNotContainA/Performance-Monitoring-and-Tuning-Tools.md)|Lists the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] monitoring and tuning tools.|  
|[Establish a Performance Baseline](../../Topics\TopicNameContainA/Establish-a-Performance-Baseline.md)|Provides information about how to establish a performance baseline.|  
|[Isolate Performance Problems](../../Topics\TopicNameNotContainA/Isolate-Performance-Problems.md)|Describes how to isolate database performance problems.|  
|[Identify Bottlenecks](../../Topics\TopicNameNotContainA/Identify-Bottlenecks.md)|Describes how to monitor and track server performance to identify bottlenecks.|  
|[Server Performance and Activity Monitoring](../../Topics\TopicNameNotContainA/Server-Performance-and-Activity-Monitoring.md)|Describes how to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows performance and activity monitoring tools.|  
|[Display and Save Execution Plans](../../Topics\TopicNameNotContainA/Display-and-Save-Execution-Plans.md)|Describes how to display and save execution plans to a file in XML format.|  
|[Live Query Statistics](../../Topics\TopicNameNotContainA/Live-Query-Statistics.md)|Describes how to display real\-time statistics about query execution steps.|  
|[Monitoring Performance By Using the Query Store](../../Topics\TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md)|The Query Store automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.|  
|[Using the Query Store with In-Memory OLTP](../../Topics\TopicNameNotContainA/Using-the-Query-Store-with-In-Memory-OLTP.md)|Provided special information about Memory\-Optimized tables.|  
|[Best Practice with the Query Store](../../Topics\TopicNameNotContainA/Best-Practice-with-the-Query-Store.md)|Provides advice on using the Query Store.|  
  
## See Also  
 [Automated Administration Across an Enterprise](../Topic/Automated%20Administration%20Across%20an%20Enterprise.md)   
 [Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Database-Engine-Tuning-Advisor.md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  