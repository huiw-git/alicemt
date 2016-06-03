---
title: View Filter Information (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
---
# View Filter Information (Transact-SQL)
  This topic describes how to use built\-in functions to view trace filter information.  
  
### To view filter information  
  
1.  Execute **fn\_trace\_getfilterinfo** by specifying the ID of the trace about which filter information is needed. This function returns a table that lists the filters, the columns on which the filters are applied, and the values on which the filter is applied.  
  
     Invoke the function this way:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## See Also  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../Topic/sys.fn_trace_getfilterinfo%20\(Transact-SQL\).md)   
 [System Stored Procedures &#40;Transact-SQL&#41;](../Topic/System%20Stored%20Procedures%20\(Transact-SQL\).md)   
 [SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](../Topic/SQL%20Server%20Profiler%20Stored%20Procedures%20\(Transact-SQL\).md)  
  
  