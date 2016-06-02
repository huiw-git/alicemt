---
title: Transact-SQL Breakpoints
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
---
# Transact-SQL Breakpoints
  Breakpoints specify that the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger pause execution on a specific [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement, you can then view the state of the code elements at that point.  
  
## Breakpoints  
 When running the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger, you can toggle a breakpoint on specific statements. When execution reaches a statement with a breakpoint, the debugger pauses execution so you can view debugging information, such as the values present in variables and parameters.  
  
 You can manage breakpoints individually in the editor window, or collectively by using the **Breakpoints** window. You can edit breakpoints to specify items such as specific conditions under which execution should pause, or the actions to be taken if the breakpoint is executed.  
  
## Breakpoint Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to specify the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement on which you want the debugger to pause.|[Toggle a Breakpoint](../../Topics\TopicNameContainA/Toggle-a-Breakpoint.md)|  
|Describes how to temporarily deactivate a breakpoint, and later reactivate it. Also describes how to delete a breakpoint.|[Enable, Disable, and Delete Breakpoints](../../Topics\TopicNameNotContainA/Enable,-Disable,-and-Delete-Breakpoints.md)|  
|Describes how to specify a condition, which defines whether breakpoint breaks based on the evaluation of a specified Transact\-SQL expression.|[Specify a Breakpoint Condition](../../Topics\TopicNameContainA/Specify-a-Breakpoint-Condition.md)|  
|Describes how to specify a hit count, which causes a breakpoint to break only when the statement containing the breakpoint has been executed a specified number of times.|[Specify a Hit Count](../../Topics\TopicNameContainA/Specify-a-Hit-Count.md)|  
|Describes how to specify a filter, which causes a breakpoint to break for only specified processes or threads.|[Specify a Breakpoint Filter](../../Topics\TopicNameContainA/Specify-a-Breakpoint-Filter.md)|  
|Describes how to specify a **When Hit** action, which is a custom operation that is performed when the breakpoint statement is executed. An example would be to print a message.|[Specify a Breakpoint Action](../../Topics\TopicNameContainA/Specify-a-Breakpoint-Action.md)|  
|Describes how to edit the location of a breakpoint.|[Edit a Breakpoint Location](../../Topics\TopicNameContainA/Edit-a-Breakpoint-Location.md)|  
  
## See Also  
 [Transact-SQL Debugger Information](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger-Information.md)  
  
  