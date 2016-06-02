---
title: Locals Window
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
---
# Locals Window
  The **Locals** window displays information about the local expressions in the current scope of the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger. The scope is set to the current call stack frame that is selected in the **Call Stack** window. You must be in debug mode to display the local expressions.  
  
## Task List  
 **To access the Locals window**  
  
-   On the **Debug** menu, click **Windows**, and then click **Locals**.  
  
 **To change the value of an expression**  
  
-   Right\-click the expression, and then select **Edit Value**.  
  
## Columns  
 **Name**  
 Is the name of the local expression. The [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger lists variables, parameters, and the system functions that have names that start with @@.  
  
 **Value**  
 Displays the value that is currently assigned to the local expression. This column is blank when no value has been assigned to the expression.  
  
 If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.  
  
 A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger visualizer is available. In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**. To start a debugger visualizer, click the magnifying glass icon. The [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.  
  
 **Type**  
 Displays the data type of the expression.  
  
## See Also  
 [Transact-SQL Debugger](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger.md)   
 [Transact-SQL Debugger Information](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger-Information.md)   
 [Watch Window](../../Topics\TopicNameNotContainA/Watch-Window.md)   
 [Call Stack Window](../../Topics\TopicNameNotContainA/Call-Stack-Window.md)   
 [QuickWatch Dialog Box](../../Topics\TopicNameNotContainA/QuickWatch-Dialog-Box.md)   
 [Expressions &#40;Transact-SQL&#41;](../Topic/Expressions%20\(Transact-SQL\).md)  
  
  