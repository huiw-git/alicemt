---
title: Create Profiler Traces for Replay (Analysis Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93b2fc46-7cfb-4ab5-abeb-1475a7d6f0f2
---
# Create Profiler Traces for Replay (Analysis Services)
  To replay queries, discovers, and commands that are submitted by users to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] must gather the required events. In order to initiate collection of these events, appropriate event classes must be selected in the **Event Selection** tab of the **Trace Properties** dialog box. For example if the Query Begin event class is selected, events that contain queries are collected and used for replay. Also, the trace file contains sufficient information to support replaying server transactions in a distributed environment in the original sequence of transactions.  
  
## Replay for Queries  
 To replay queries, [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] must capture the following events:  
  
-   Audit Login event class with all its data columns. This event class provides information about which user logged in and about the session settings. The server process ID \(SPID\) provides the reference to the user session. For more information, see [Security Audit Data Columns](../../Topics\TopicNameNotContainA/Security-Audit-Data-Columns.md).  
  
-   Query Begin event class with all its data columns. This event class provides information about the query that was submitted to [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. The Event Subclass column provides information about the type of query. The TextData column provides the actual text of the query. The RequestParameters column provides the parameters for parameterized queries, and the RequestProperties column provides the properties of an XML for Analysis \(XMLA\) request. For more information, see [Queries Events Data Columns](../../Topics\TopicNameNotContainA/Queries-Events-Data-Columns.md).  
  
-   Query End event class with all its data columns. This event class verifies the status of the query execution. For more information, see [Queries Events Data Columns](../../Topics\TopicNameNotContainA/Queries-Events-Data-Columns.md).  
  
## Replay for Discovers  
 To replay discovers, [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] must capture the following events:  
  
-   Audit Login event class with all its data columns. This event class provides information about which user logged in and about the session settings. The SPID provides the reference to the user session. For more information, see [Security Audit Data Columns](../../Topics\TopicNameNotContainA/Security-Audit-Data-Columns.md).  
  
-   Discover Begin event class with all its data columns. The TextData column provides the \<RequestType\> portion of the discover request, and the RequestProperties column provides the \<Properties\> portion of the discover request. The EventSubclass column provides the discover type. For more information, see [Discover Events Data Columns](../../Topics\TopicNameNotContainA/Discover-Events-Data-Columns.md).  
  
-   Discover End event class with all its data columns. This event class verifies the status of the discover request. For more information, see [Discover Events Data Columns](../../Topics\TopicNameNotContainA/Discover-Events-Data-Columns.md).  
  
## Replay for Commands  
 To replay commands, [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] must capture the following events:  
  
-   Command Begin event class with all its data columns. The TextData column provides the command details, such as the process type, database ID, and cube ID. The RequestParameters column provides the parameters for parameterized command, and the RequestProperties column provides the properties of an XMLA request. For more information, see [Command Events Data Columns](../../Topics\TopicNameNotContainA/Command-Events-Data-Columns.md).  
  
-   Command End event class with all its data columns. This event class verifies the status of the command. For more information, see [Command Events Data Columns](../../Topics\TopicNameNotContainA/Command-Events-Data-Columns.md).  
  
## See Also  
 [Analysis Services Trace Events](../../Topics\TopicNameNotContainA/Analysis-Services-Trace-Events.md)   
 [Introduction to Monitoring Analysis Services with SQL Server Profiler](../../Topics\TopicNameNotContainA/Introduction-to-Monitoring-Analysis-Services-with-SQL-Server-Profiler.md)  
  
  