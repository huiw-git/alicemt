---
title: "Natively Compiled Stored Procedures and Execution Set Options"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
caps.latest.revision: 6
caps.handback.revision: 0
manager: jhubbard
---
# Natively Compiled Stored Procedures and Execution Set Options
Session options are fixed in atomic blocks. A stored procedure's execution is not affected by a session's SET options. However, certain SET options, such as SET NOEXEC and SET SHOWPLAN_XML, cause stored procedures (including natively compiled stored procedures) to not execute.  
  
 When a natively compiled stored procedure is executed with any STATISTICS option turned on, statistics are gathered for the procedure as a whole and not per statement. For more information, see [SET STATISTICS IO (Transact-SQL)](assetId:///7033aac9-a944-4156-9ff4-6ef65717a28b), [SET STATISTICS PROFILE (Transact-SQL)](assetId:///c635e262-35fa-421a-aa6f-a1c30f351647), [SET STATISTICS TIME (Transact-SQL)](assetId:///eec2e1cd-a29d-4cf3-a271-be9d61506f15), and [SET STATISTICS XML (Transact-SQL)](assetId:///2b6d4c5a-a7f5-4dd1-b10a-7632265b1af7). To obtain execution statistics on a per-statement level in natively compiled stored procedures, use an Extended Event session on the sp_statement_completed event, which starts when each individual query in a stored procedures execution completes. For more information on creating Extended Event sessions, see [CREATE EVENT SESSION](assetId:///67683027-2b0f-47aa-b223-604731af8b4d).  
  
 **SHOWPLAN_XML** is supported for natively compiled stored procedures. **SHOWPLAN_ALL** and **SHOWPLAN_TEXT** are not supported with natively compiled stored procedures.  
  
 **SET FMTONLY** in not supported with natively compiled stored procedures. Use [sp_describe_first_result_set (Transact-SQL)](assetId:///f2355a75-3a8e-43e6-96ad-4f41038f6d22) instead.  
  
## See Also  
 [Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)