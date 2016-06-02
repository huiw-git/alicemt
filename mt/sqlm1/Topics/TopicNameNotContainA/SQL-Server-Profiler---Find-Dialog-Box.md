---
title: SQL Server Profiler - Find Dialog Box
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
---
# SQL Server Profiler - Find Dialog Box
  Use the **Find** dialog box to search a trace for specific characters or words. To cancel a search in progress, press ESC.  
  
 To open this dialog box in [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], on the **Edit** menu, click **Find**.  
  
## Options  
 **Find what**  
 Enter the text that you want to search for. The search matches any string containing the specified string. For example, searching for "Completed" matches "SQL:BatchCompleted." Wild card characters \(\*, ?, etc.\) are not supported.  
  
 **Search in column**  
 Click a data column to search, or click **\<All columns\>** to search all the data columns in the trace.  
  
 **Match case**  
 Finds text that has the same case as the **Find what** box. Clear this check box to find examples in the trace that are in both uppercase and lowercase text characters.  
  
 **Match whole word**  
 Restricts the search to entire words. Clear the **Match whole word** check box to search for characters within a word.  
  
 **Find Next**  
 Finds the next example of the characters in the **Find what** box.  
  
 **Find Previous**  
 Searches backwards in the trace, to find the previous example of the characters in the **Find what** box.  
  
## See Also  
 [Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;](../Topic/Find%20a%20Value%20or%20Data%20Column%20While%20Tracing%20\(SQL%20Server%20Profiler\).md)   
 [Create a Trace &#40;SQL Server Profiler&#41;](../Topic/Create%20a%20Trace%20\(SQL%20Server%20Profiler\).md)   
 [Open a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)   
 [Open a Trace File &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)   
 [SQL Server Profiler Templates and Permissions](../../Topics\TopicNameNotContainA/SQL-Server-Profiler-Templates-and-Permissions.md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  