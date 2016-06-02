---
title: Options (Text Editor/Transact-SQL/IntelliSense)
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
---
# Options (Text Editor/Transact-SQL/IntelliSense)
  The **Options** dialog box lets you change the IntelliSense settings for the [!INCLUDE[ssDE](../../../../Token\Other/ssDE_md.md)] Query Editor. These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, expand the **Transact\-SQL** folder, and then click **Advanced**.  
  
## Transact\-SQL IntelliSense Settings  
 Specifies the IntelliSense options for the [!INCLUDE[ssDE](../../../../Token\Other/ssDE_md.md)] Query Editor.  
  
### Enable IntelliSense  
 Enables the IntelliSense features. When this box is not selected, the specific IntelliSense options are unavailable. By default, this check box is selected.  
  
 **Underline errors**  
 Identifies syntax and semantic errors in [!INCLUDE[tsql](../../../../Token\Other/tsql_md.md)] statements in the query window. All errors and warnings appear in red. Errors and warnings are supported only for the [!INCLUDE[tsql](../../../../Token\Other/tsql_md.md)] statements for which IntelliSense has been implemented. By default, this check box is selected.  
  
 **Outline statements**  
 Enables the outlining feature when a file is opened. This creates collapsible blocks of [!INCLUDE[tsql](../../../../Token\Other/tsql_md.md)] code. By default, this check box is selected.  
  
 **Maximum script size**  
 Specifies the size at which IntelliSense functionality is disabled. If a script exceeds the specified size, a warning message is issued. All IntelliSense features, except color coding, are disabled for that editor window. IntelliSense is reenabled when enough text is deleted to reduce the script size to under the limit. Enabling IntelliSense for large script sizes can decrease performance on slow computers. The allowed sizes are 100 KB, 500 KB, 1 MB, 2 MB, and Unlimited. The default is 1 MB.  
  
 **Casing for built\-in function names**  
 Specifies whether the names of built\-in [!INCLUDE[tsql](../../../../Token\Other/tsql_md.md)] functions that are included in completion lists use uppercase letters, such as DATEADD; or lowercase letters, such as dateadd. Select the option that best matches the [!INCLUDE[tsql](../../../../Token\Other/tsql_md.md)] coding conventions that you are using.  
  
## See Also  
 [Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;](../Topic/Troubleshooting%20IntelliSense%20\(SQL%20Server%20Management%20Studio\).md)  
  
  