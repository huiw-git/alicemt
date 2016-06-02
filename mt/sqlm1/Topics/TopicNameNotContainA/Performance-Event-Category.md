---
title: Performance Event Category
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
---
# Performance Event Category
  Use the **Performance** event category to monitor **Showplan** event classes and event classes that are produced from the execution of SQL data manipulation language \(DML\) operators.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Auto Stats Event Class](../../Topics\TopicNameNotContainA/Auto-Stats-Event-Class.md)|Indicates that an automatic updating of index and column statistics has occurred.|  
|[Degree of Parallelism &#40;7.0 Insert&#41; Event Class](../Topic/Degree%20of%20Parallelism%20\(7.0%20Insert\)%20Event%20Class.md)|Indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has executed a SELECT, INSERT, UPDATE, or DELETE statement using either a serial or parallel plan. The number of CPUs used to perform the operation is also reported.|  
|[Performance Statistics Event Class](../../Topics\TopicNameNotContainA/Performance-Statistics-Event-Class.md)|Monitors performance of the queries that are being executed.|  
|[Showplan All Event Class](../../Topics\TopicNameNotContainA/Showplan-All-Event-Class.md)|Identifies **Showplan** operators within a SQL statement.|  
|[Showplan All for Query Compile Event Class](../../Topics\TopicNameNotContainA/Showplan-All-for-Query-Compile-Event-Class.md)|Displays compile time data for **Showplan** operators.|  
|[Showplan Statistics Profile Event Class](../../Topics\TopicNameNotContainA/Showplan-Statistics-Profile-Event-Class.md)|Displays the estimated cost of a query.|  
|[Showplan XML Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-Event-Class.md)|Identifies the **Showplan** operators in a SQL statement. The event class stores each event as a well defined XML document.|  
|[Showplan XML for Query Compile Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-for-Query-Compile-Event-Class.md)|Displays compile time data for **Showplan** operators in XML format.|  
|[Showplan XML Statistics Profile Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-Statistics-Profile-Event-Class.md)|Identifies the **Showplan** operators associated with a SQL statement. The output is an XML document.|  
|[SQL:FullTextQuery Event Class](../Topic/SQL:FullTextQuery%20Event%20Class.md)|Indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has executed a full\-text query.|  
|[Plan Guide Successful Event Class](../../Topics\TopicNameNotContainA/Plan-Guide-Successful-Event-Class.md)|Indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] successfully produced an execution plan for a query or batch that contained a plan guide.|  
|[Plan Guide Unsuccessful Event Class](../../Topics\TopicNameNotContainA/Plan-Guide-Unsuccessful-Event-Class.md)|Indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] could not produce an execution plan for a query or batch that contained a plan guide.|  
  
## See Also  
 [Extended Events](../../Topics\TopicNameNotContainA/Extended-Events.md)  
  
  