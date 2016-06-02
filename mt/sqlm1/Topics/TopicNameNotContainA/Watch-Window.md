---
title: Watch Window
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
---
# Watch Window
  The **Watch** window displays information about the expressions that you have selected. There can be up to four watch windows: **Watch 1**, **Watch 2, Watch 3**, and **Watch 4**. The expressions are evaluated within the scope of the current call stack frame that is selected in the **Call Stack** window. You must be in debug mode to watch variables and expressions.  
  
## Task List  
 **To access the Watch windows**  
  
-   On the **Debug** menu, click **Windows**, click **Watch**, and then click **Watch 1**, **Watch 2, Watch 3**, or **Watch 4**.  
  
 **To change the value of an expression**  
  
-   Right\-click the expression, and then select **Edit Value**.  
  
## Columns  
 **Name**  
 Are the expressions that are listed by the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger. The following expressions are supported:  
  
-   Variables.  
  
-   Parameters.  
  
-   System functions whose name starts with @@.  
  
-   Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter \+ 1, or FirstName \+ LastName.  
  
-   Transact\-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey \= 1.  
  
 **Value**  
 Displays the value that is returned after the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger evaluates the expression specified in **Name**.  
  
 If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.  
  
 A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger visualizer is available. In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**. To start a debugger visualizer, click the magnifying glass icon. The [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger opens a dialog that displays the data in a format appropriate to the data type.  
  
 **Type**  
 Displays the data type of the expression.  
  
## See Also  
 [Transact-SQL Debugger](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger.md)   
 [Transact-SQL Debugger Information](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger-Information.md)   
 [Locals Window](../../Topics\TopicNameNotContainA/Locals-Window.md)   
 [Call Stack Window](../../Topics\TopicNameNotContainA/Call-Stack-Window.md)   
 [QuickWatch Dialog Box](../../Topics\TopicNameNotContainA/QuickWatch-Dialog-Box.md)   
 [Expressions &#40;Transact-SQL&#41;](../Topic/Expressions%20\(Transact-SQL\).md)  
  
  