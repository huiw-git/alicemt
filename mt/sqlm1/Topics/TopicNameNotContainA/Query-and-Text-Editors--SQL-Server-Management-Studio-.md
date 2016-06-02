---
title: Query and Text Editors (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 062051e4-4b77-4969-98ae-d2547c24ce3e
---
# Query and Text Editors (SQL Server Management Studio)
  You can use one of the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] editors to interactively edit and test a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], MDX, DMX, or XML\/A script, or to edit an XML or plain text file. Each editor is supported by a language\-specific service that colors keywords, and checks for syntax and usage errors. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor includes a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger that you can use to help fix problems in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] code.  
  
## SQL Server Management Studio Editors  
 The four editors in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] share a common architecture. The text editor implements the base level of functionality, and can be used as a basic editor for text files. The other three editors, or query editors, extend this base of functionality by including a language service that defines the syntax of one of the languages supported in SQL Server. The query editors also implement varying levels of support for editor features such as IntelliSense and debugging. The query editors include the Database Engine Query Editor for use in building scripts containing Transact\-SQL and XQuery statements, the MDX editor for the MDX language, the DMX editor for the DMX language, and the XML\/A editor for the XML for Analysis language.  
  
## Common Components  
 All of the editors in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] share these components:  
  
 **Code Pane**  
 The area where you enter your queries or text. In the query editors, it contains the statement builder features available for your language. The text editing environment supports find and replace, bulk commenting, and custom fonts and colors.  
  
 You can set options that affect the behavior of text in the code pane as it relates to indenting, tabbing, dragging and dropping of text, and so forth. Query windows can be configured to operate as either tabs in the document window, or in separate documents.  
  
 **Selection Margin**  
 A column of white space between the margin indicator bar and the code text where you can click to select lines of text. You can hide or display the selection margin.  
  
 **Horizontal and Vertical Scroll Bars**  
 Allows you to scroll the code pane horizontally and vertically so that you can view the code that extends beyond the viewable edges of the code pane.  
  
 **Line Numbering**  
 Displays line numbers to the left of the text or code in the Editor. You can navigate to specific line numbers.  
  
 **Word Wrap**  
 Displays long lines of text or code as multiple lines, enabling you to see all the text on the line. Word wrap does not affect the way text appears when it is executed or printed. Word wrap is turned on from the **Tools**, **Options** dialog box, on either the Text Editor, All Languages, General page, or on a specific editor page.  
  
## Code Editor Components  
 The code editors contain these features in addition to the ones shared with the text and XML editors:  
  
 **Results**  
 This window is used to view the results of a query. The window can display the results in grid or in text, or the results can be directed to a file. Result grids can be displayed as separate tabbed windows.  
  
 **IntelliSense**  
 In the Editors, on the **Edit** menu, point to **IntelliSense**, to view the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] IntelliSense options.  
  
 **Color Coding**  
 Displays different colors for each type of syntax element, which improves the readability of complex statements.  
  
 **Code Outlining**  
 Displays code groups with outlining lines to the left of the code. Code groups can be collapsed and expanded to make it easier to review your code.  
  
 **Template**  
 Templates are files that include the basic structure of the statements needed to create objects in a database. They can be used to speed the authoring of scripts.  
  
 **Messages**  
 Displays errors, warnings, and informational messages that are returned by the server when a script is run. The list of messages does not change until the script is run again.  
  
 **Status Bar**  
 Displays system information that is associated with the Query Editor window, such as which instance the Query Editor is connected to.  
  
## Database Engine Query Editor Components  
 These components are only available in the Database Engine Query Editor:  
  
 **Debugger**  
 Enables you to pause the execution of code on specific statements. You can then view data and system information to help you find errors in the code.  
  
 **Error List**  
 Displays syntax and semantic errors found by IntelliSense. The list of errors changes dynamically as you edit [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts.  
  
 **Graphical Showplan**  
 Displays the logical steps built into the execution plan of a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement.  
  
 **Client Statistics**  
 Displays information about the query execution grouped into categories. When **Include Client Statistics** is selected from the **Query** menu, a **Client Statistics** window is displayed upon query execution. Statistics from successive query executions are listed along with the average values. Select **Reset Client Statistics** from the **Query** menu to reset the average.  
  
 **Code Snippets**  
 Templates you can use as a starting point when adding statements in the Database Engine Query Editor. You can insert the pre\-defined snippets supplied with SQL Server, or add your own snippets.  
  
 **SQLCMD Mode**  
 Runs [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts that include the set of commands supported by the sqlcmd utility. For more information, see [sqlcmd How-to Topics](../../Topics\TopicNameNotContainA/sqlcmd-How-to-Topics.md).  
  
## Editor Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to view and use the basic features in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor.|[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../Topic/Database%20Engine%20Query%20Editor%20\(SQL%20Server%20Management%20Studio\).md)|  
|Describes how to view and use the basic features in the MDX Query Editor.|[MDX Query Editor &#40;Analysis Services - Multidimensional Data&#41;](../Topic/MDX%20Query%20Editor%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)|  
|Describes how to view and use the basic features in the DMX Query Editor.|[DMX Query Editor &#40;Analysis Services - Data Mining&#41;](../Topic/DMX%20Query%20Editor%20\(Analysis%20Services%20-%20Data%20Mining\).md)|  
|Describes how to view and use the basic features in the XML\/A Editor.|[XML Editor &#40;SQL Server Management Studio&#41;](../Topic/XML%20Editor%20\(SQL%20Server%20Management%20Studio\).md)|  
|Describes how to configure options for the various editors, such as line numbering and IntelliSense options.|[Configure Editors &#40;SQL Server Management Studio&#41;](../Topic/Configure%20Editors%20\(SQL%20Server%20Management%20Studio\).md)|  
|Describes the various ways you can open the editors in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)].|[Open an Editor &#40;SQL Server Management Studio&#41;](../Topic/Open%20an%20Editor%20\(SQL%20Server%20Management%20Studio\).md)|  
|Describes how to manage the view mode, such as word wrap, splitting a window, or tabs.|[Manage the Editor and View Mode](../../Topics\TopicNameNotContainA/Manage-the-Editor-and-View-Mode.md)|  
|Describes how to set formatting options, such as hidden text or indentation.|[Manage Code Formatting](../../Topics\TopicNameNotContainA/Manage-Code-Formatting.md)|  
|Describes how to navigate through the text in an editor window by using features such as incremental search or go to.|[Navigate Code and Text](../../Topics\TopicNameNotContainA/Navigate-Code-and-Text.md)|  
|Describes how to set color coding options for various classes of syntax, which makes it easier to read complex statements.|[Color Coding in Query Editors](../../Topics\TopicNameNotContainA/Color-Coding-in-Query-Editors.md)|  
|Describes how to use code outlining to hide parts of complex scripts that you are not currently working on.|[Code Outlining](../../Topics\TopicNameNotContainA/Code-Outlining.md)|  
|Describes how to drag text from one location in a script and drop it in a new location.|[Drag and Drop Text](../../Topics\TopicNameNotContainA/Drag-and-Drop-Text.md)|  
|Describes how to do global search and replace, such as when changing column names.|[Search and Replace](../../Topics\TopicNameNotContainA/Search-and-Replace.md)|  
|Describes how to set bookmarks in order to more easily find important pieces of code.|[Manage Bookmarks](../../Topics\TopicNameNotContainA/Manage-Bookmarks.md)|  
|Describes how to print scripts or the results in a window or grid.|[Print Code and Results](../../Topics\TopicNameNotContainA/Print-Code-and-Results.md)|  
|Describes how to use the sqlcmd features in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor.|[Edit SQLCMD Scripts with Query Editor](../../Topics\TopicNameNotContainA/Edit-SQLCMD-Scripts-with-Query-Editor.md)|  
|Describes how to use IntelliSense features such as auto\-completing object names as you type them, or ensuring breakpoints are placed in valid locations.|[IntelliSense &#40;SQL Server Management Studio&#41;](../Topic/IntelliSense%20\(SQL%20Server%20Management%20Studio\).md)|  
|Describes how to use code snippets in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor. Snippets are templates for commonly used statements or blocks, and can be customized or extended to include site\-specific snippets.|[Transact-SQL Code Snippets](../../Topics\TopicNameNotContainA/Transact-SQL-Code-Snippets.md)|  
|Describes how to use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] debugger to step through code and view debugging information such as the values in variables and parameters.|[Transact-SQL Debugger](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger.md)|  
|Describes how to set custom colors for different instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], and have those colors set as the background of the status bar in [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor windows.|[Status Bar &#40;Database Engine Query Editor&#41;](../Topic/Status%20Bar%20\(Database%20Engine%20Query%20Editor\).md)|  
  
## See Also  
 [SQL Server Management Studio Keyboard Shortcuts](../../Topics\TopicNameNotContainA/SQL-Server-Management-Studio-Keyboard-Shortcuts.md)  
  
  