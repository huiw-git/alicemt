---
title: Delete a Trace (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
---
# Delete a Trace (Transact-SQL)
  This topic describes how to use stored procedures to delete a trace.  
  
 For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](../Topic/Create%20a%20Trace%20\(Transact-SQL\).md).  
  
### To delete a trace  
  
1.  Execute **sp\_trace\_setstatus** by specifying **@status \= 0** to stop the trace.  
  
2.  Execute **sp\_trace\_setstatus** by specifying **@status \= 2** to close the trace and delete its information from the server.  
  
> [!NOTE]  
>  A trace must be stopped first before it can be closed.  
  
## See Also  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../Topic/sp_trace_setstatus%20\(Transact-SQL\).md)   
 [System Stored Procedures &#40;Transact-SQL&#41;](../Topic/System%20Stored%20Procedures%20\(Transact-SQL\).md)   
 [SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](../Topic/SQL%20Server%20Profiler%20Stored%20Procedures%20\(Transact-SQL\).md)  
  
  