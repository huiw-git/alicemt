---
title: Analyze Queries with SHOWPLAN Results in SQL Server Profiler
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a2f7727-141c-4f59-8613-2e452bc78467
---
# Analyze Queries with SHOWPLAN Results in SQL Server Profiler
  You can add Showplan event classes to a trace definition that cause [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to gather and display query plan information in the trace. It is also possible to extract Showplan events from the other events collected in the trace and to save these Showplan events in a separate XML file.  
  
 Extracting Showplan events from the trace can be done in any of the following ways:  
  
-   At trace configuration time, using the **Events Extraction Settings** tab. Note that this tab does not appear until you select a one of the Showplan events on the **Events Selection** tab.  
  
-   Using the **Extract SQL Server Events** option on the **File** menu.  
  
-   By extracting and saving individual events by right\-clicking a specific event and choosing **Extract Event Data**.  
  
## Showplan Events  
 The Showplan trace events are listed and described in the following table.  
  
|Event name|Description|  
|----------------|-----------------|  
|**Performance statistics**|Indicates the first time a compiled Showplan is cached, when it is recompiled, and when it is dropped from the plan cache. The **TextData** column contains the Showplan in XML format. For more information, see [Performance Statistics Event Class](../../Topics\TopicNameNotContainA/Performance-Statistics-Event-Class.md).|  
|**Showplan All**|Displays the query plan with full compilation details of the executed [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement. For example, it might display costing estimates and column lists. For more information, see [Showplan All Event Class](../../Topics\TopicNameNotContainA/Showplan-All-Event-Class.md).|  
|**Showplan All For Query Compile**|Occurs when a query is compiled or recompiled on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This is the compile time counterpart of the **Showplan All** event. **Showplan All** occurs when a query is executed. **Showplan All For Query Compile** occurs when a query is compiled. For more information, see [Showplan All for Query Compile Event Class](../../Topics\TopicNameNotContainA/Showplan-All-for-Query-Compile-Event-Class.md).|  
|**Showplan Statistics Profile**|Displays the query plan with full run\-time details of the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement being executed, including the actual number of rows passing through each operation. For more information, see [Showplan Statistics Profile Event Class](../../Topics\TopicNameNotContainA/Showplan-Statistics-Profile-Event-Class.md).|  
|**Showplan Text**|Displays as binary data the query plan tree of the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement being executed. For more information, see [Showplan Text Event Class](../../Topics\TopicNameNotContainA/Showplan-Text-Event-Class.md).|  
|**Showplan Text \(Unencoded\)**|Displays as text the query plan tree of the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement being executed. This event class displays the same information as Showplan Text, except that this event class displays text instead of binary data. For more information, see [Showplan Text &#40;Unencoded&#41; Event Class](../Topic/Showplan%20Text%20\(Unencoded\)%20Event%20Class.md).|  
|**Showplan XML**|Displays the query plan with full data collected during query optimization. This event is generated only when a query plan is optimized. For more information, see [Showplan XML Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-Event-Class.md).|  
|**Showplan XML For Query Compile**|Displays the query plan when the query is compiled. For more information, see [Showplan XML for Query Compile Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-for-Query-Compile-Event-Class.md).|  
|**Showplan XML Statistics Profile**|Displays the query plan with full run\-time details in XML format. For example, this event class captures the number of rows passing through each operator of the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement that is executed. For more information, see [Showplan XML Statistics Profile Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-Statistics-Profile-Event-Class.md).|  
  
## See Also  
 [Performance Event Category](../../Topics\TopicNameNotContainA/Performance-Event-Category.md)  
  
  