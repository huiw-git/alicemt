---
title: Command Window
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
---
# Command Window
  Use the **CommandWindow** to run commands, such as debug and edit commands, against the code in the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] Query Editor window that is currently being debugged. You must be in debug mode to use the **Command Window**. The [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger supports many of the commands that are also supported in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)] **Command** window. For more information, see [Visual Studio Command Window](http://go.microsoft.com/fwlink/?LinkId=112007).  
  
## Task List  
 **To access the Command Window**  
  
-   On the **Debug** menu, click **Start Debugging**.  
  
 **To print the value of a variable**  
  
-   In the **CommandWindow**, type **Debug.Print \<VariableName\>**, and then press ENTER.  
  
 **To list information about the current thread**  
  
-   In the **CommandWindow**, type **Debug.ListThread**, and then press ENTER.  
  
 **To add a variable to the QuickWatch window**  
  
-   In the **CommandWindow**, type **Debug.QuickWatch \<VariableName\>**, and then press ENTER.  
  
## See Also  
 [Transact-SQL Debugger](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger.md)  
  
  