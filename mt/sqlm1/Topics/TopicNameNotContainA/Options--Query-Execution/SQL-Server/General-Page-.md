---
title: Options (Query Execution/SQL Server/General Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f8d59bc-3f97-4e5d-8b86-5ac670d20780
---
# Options (Query Execution/SQL Server/General Page)
  Use this page to specify the options for running [!INCLUDE[ssNoVersion](../../../../Token\Other/ssNoVersion_md.md)] queries. Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../../../../Token\Other/ssNoVersion_md.md)] queries. To change the options for a current query, click **Query Options** on the **Query** menu, or in a [!INCLUDE[ssNoVersion](../../../../Token\Other/ssNoVersion_md.md)] Query window right\-click and select **Query Options**.  
  
## Options  
 **SET ROWCOUNT**  
 The default value of 0 indicates that [!INCLUDE[ssNoVersion](../../../../Token\Other/ssNoVersion_md.md)] will wait for results until all results are received. Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../../../../Token\Other/ssNoVersion_md.md)] to halt the query after obtaining the specified number of rows. To turn this option off \(so that all rows are returned\), specify SET ROWCOUNT 0.  
  
 **SET TEXTSIZE**  
 The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../../../../Token\Other/ssNoVersion_md.md)] will provide complete data fields up to the limit of **text** and **ntext** data fields. Provide a smaller number to limit results in the case of large values. Columns greater than the number provided will be truncated.  
  
 **Execution time\-out**  
 Sets the default value in the **New Connection** dialog box. Use this spin box to tell [!INCLUDE[ssNoVersion](../../../../Token\Other/ssNoVersion_md.md)] the number of seconds to wait before canceling the query. A value of 0 indicates an infinite wait, or no time\-out. This value is 0 on a new installation.  
  
 **Batch separator**  
 Type a word that you use to separate [!INCLUDE[tsql](../../../../Token\Other/tsql_md.md)] statements into batches. The default is GO.  
  
 **By default, open new queries in SQLCMD Mode**  
 Select this check box to open new queries in SQLCMD mode. For more information about SQLCMD mode, see [Edit SQLCMD Scripts with Query Editor](../../../../Topics\TopicNameNotContainA/Edit-SQLCMD-Scripts-with-Query-Editor.md).  
  
 When you select this option, be aware of the following limitations:  
  
-   IntelliSense in the [!INCLUDE[ssDE](../../../../Token\Other/ssDE_md.md)] Query Editor is turned off.  
  
-   Because Query Editor does not run from the command line, you cannot pass in command\-line parameters such as variables.  
  
-   Because Query Editor cannot respond to operating\-system prompts, you must be careful not to run interactive statements.  
  
 **Reset to Default**  
 Click to reset all values on this page to the original default values.  
  
## See Also  
 [sqlcmd Utility](../../../../Topics\TopicNameNotContainA/sqlcmd-Utility.md)  
  
  