---
title: "View Filter Information (Transact-SQL)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# View Filter Information (Transact-SQL)
This topic describes how to use built-in functions to view trace filter information.  
  
### To view filter information  
  
1.  Execute **fn_trace_getfilterinfo** by specifying the ID of the trace about which filter information is needed. This function returns a table that lists the filters, the columns on which the filters are applied, and the values on which the filter is applied.  
  
     Invoke the function this way:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## See Also  
 [SQL Server Profiler Stored Procedures (Transact-SQL)](assetId:///09fe4a28-ff8a-4655-9da1-4654d5bc514d)   
 [System Stored Procedures](assetId:///a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a)   
 [SQL Server Profiler Stored Procedures (Transact-SQL)](assetId:///8c99c3db-0b04-46c3-aa59-d6f680522fdd)