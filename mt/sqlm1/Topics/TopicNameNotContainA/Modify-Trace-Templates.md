---
title: Modify Trace Templates
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
---
# Modify Trace Templates
  You can modify templates that are saved in a file on the local computer on which [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] is running. You can also modify templates derived from those files. When you modify existing templates, you edit template properties such as event classes and data columns, in the same order that the properties were set originally, on the **Events Selection** tab of the **Trace Properties** dialog box. Event classes and data columns can be added or removed, and filters can be changed. After the template is modified, a user\-specific template is created and the original system template is left intact. For more information, see [Save Traces and Trace Templates](../../Topics\TopicNameNotContainA/Save-Traces-and-Trace-Templates.md).  
  
 You may need to derive a template from an existing trace file if you cannot remember \(or have not saved\) the original template that was used to create the trace, or if you want to run the same trace at a later date. When working with existing traces, you can view the properties, but you cannot modify the properties. To modify the properties, stop or pause the trace. For more information, see [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../Topic/Derive%20a%20Template%20from%20a%20Trace%20File%20or%20Trace%20Table%20\(SQL%20Server%20Profiler\).md) and [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../Topic/Derive%20a%20Template%20from%20a%20Running%20Trace%20\(SQL%20Server%20Profiler\).md).  
  
 **To create a trace template**  
  
 [Create a Trace Template &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)  
  
 **To run a trace from a trace template**  
  
 [Create a Trace &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
 **To modify a trace template**  
  
 [Using SQL Server Profiler](../Topic/Modify%20a%20Trace%20Template%20\(SQL%20Server%20Profiler\).md)  
  
 [Using Transact\-SQL](../Topic/Modify%20an%20Existing%20Trace%20\(Transact-SQL\).md)  
  
 **To add or remove events from a trace template or trace file**  
  
 [Using SQL Server Profiler](../Topic/Specify%20Events%20and%20Data%20Columns%20for%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)  
  
 [Using Transact\-SQL](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)  
  
## See Also  
 [Start a Trace](../../Topics\TopicNameContainA/Start-a-Trace.md)  
  
  