---
title: Options (Query Execution/SQL Server/Live Query Statistics Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c96aa09a-b399-428d-bbe3-0cd2da714e1d
---
# Options (Query Execution/SQL Server/Live Query Statistics Page)
  This page configures the options for live query statistics. The live query plan displays the overall query progress and the run\-time execution statistics \(e.g. elapsed time, progress, etc.\) for the query plan operators. The query progress information and execution statistics are periodically updated while query execution is in progress. Use this information to understand the overall query execution process and to debug long running queries, queries that run indefinitely, queries that cause tempdb overflow, and timeout issues. For more information, see [Live Query Statistics](../../../../Topics\TopicNameNotContainA/Live-Query-Statistics.md).  
  
## UIElement List  
 **Compilation Polling Interval \(milliseconds\)**  
 Configures the frequency of the aggregation and updating of the live query statistics.  
  
 **Node Polling Interval \(milliseconds\)**  
 Configures the frequency that live query statistics checks for more information.  
  
  