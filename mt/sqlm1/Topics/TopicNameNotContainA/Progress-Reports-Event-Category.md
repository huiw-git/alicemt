---
title: Progress Reports Event Category
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
---
# Progress Reports Event Category
  The Progress Reports event category has the event classes described in the following table.  
  
|Event Class|Event Id|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|Collects all progress report begin events since the trace was started.|  
|Progress Report End|6|Collects all progress report end events since the trace was started.|  
|Progress Report Current|7|Collects all progress report current events since the trace was started. For example, during processing, current reports include processing information about objects being processed \(dimensions, partitions, cube, etc\).|  
|Progress Report Error|8|Collects all progress report error events since the trace was started.|  
  
 Each Progress Report Begin event begins with a stream of progress events and is terminated with a Progress Report End event. The stream may contain any number of Progress Report Current and Progress Report Error events.  
  
 For information about the columns associated with each of the Progress Reports event classes, see [Progress Reports Data Columns](../../Topics\TopicNameNotContainA/Progress-Reports-Data-Columns.md).  
  
## See Also  
 [Analysis Services Trace Events](../../Topics\TopicNameNotContainA/Analysis-Services-Trace-Events.md)  
  
  