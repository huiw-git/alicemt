---
title: Reporting Services Query Designers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
robots: noindex,nofollow
---
# Reporting Services Query Designers
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides graphical and text\-based query designers to help you build queries for each data source type in your report.  
  
 Some data sources support graphical designers that help you build a query interactively. Other data sources use a text\-based query designer. By using a graphical query designer, you can drag metadata items that represent the underlying data on a data source to the query design surface. By using a text\-based query designer, you can type command text into a query pane. You can change from a graphical query designer to a text\-based query designer by clicking the text\-based query designer icon on the toolbar.  
  
 The data source types that are available in your report are determined by the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] data extensions installed on your client or report server. For more information, see [RSReportDesigner Configuration File](../../Topics\TopicNameNotContainA/RSReportDesigner-Configuration-File.md) and [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md).  
  
 A data processing extension and its associated query designer can differ in support for data sources in the following ways:  
  
-   **By query designer type.** For example, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data source supports both the graphical and text\-based query designers.  
  
-   **By query language variation.** For example, a query language such as [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] can differ in syntax depending on the data source type. The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] language and the Oracle SQL language have some variation in syntax for a query command.  
  
-   **By support for the schema part of a database object name.** When a data source uses schemas as part of the database object identifier, the schema name must be supplied as part of the query for any names that do not use the default schema. For example, `SELECT FirstName, LastName FROM [Person].[Person]`.  
  
-   **By support for query parameters.** Data providers differ in support for parameters. Some data providers support named parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`. Some data providers support unnamed parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`. The parameter identifier might differ by data provider; for example, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses the "at" \(@\) symbol, Oracle uses the colon \(:\). Some data providers do not support parameters.  
  
-   **By ability to import queries.** For example, for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data source, you can import a query from a report definition file \(.rdl\) or from a .sql file.  
  
## Query Designers  
 The following topics describe the user interface for each query designer.  
  
-   [Analysis Services MDX Query Designer User Interface](../../Topics\TopicNameNotContainA/Analysis-Services-MDX-Query-Designer-User-Interface.md)  
  
-   [Analysis Services DMX Query Designer User Interface](../../Topics\TopicNameNotContainA/Analysis-Services-DMX-Query-Designer-User-Interface.md)  
  
-   [Graphical Query Designer User Interface](../../Topics\TopicNameNotContainA/Graphical-Query-Designer-User-Interface.md)  
  
-   [Relational Query Designer User Interface](../../Topics\TopicNameNotContainA/Relational-Query-Designer-User-Interface.md)  
  
-   [Hyperion Essbase Query Designer User Interface](../../Topics\TopicNameNotContainA/Hyperion-Essbase-Query-Designer-User-Interface.md)  
  
-   [Report Model Query Designer User Interface](../../Topics\TopicNameNotContainA/Report-Model-Query-Designer-User-Interface.md)  
  
-   [SAP NetWeaver BI Query Designer User Interface](../../Topics\TopicNameNotContainA/SAP-NetWeaver-BI-Query-Designer-User-Interface.md)  
  
-   [SharePoint List Query Designer](../../Topics\TopicNameNotContainA/SharePoint-List-Query-Designer.md)  
  
-   [Text-based Query Designer User Interface](../../Topics\TopicNameNotContainA/Text-based-Query-Designer-User-Interface.md)  
  
## See Also  
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md)   
 [Add Data from External Data Sources &#40;SSRS&#41;](../Topic/Add%20Data%20from%20External%20Data%20Sources%20\(SSRS\).md)   
 [Data Processing Extensions and .NET Framework Data Providers &#40;SSRS&#41;](../Topic/Data%20Processing%20Extensions%20and%20.NET%20Framework%20Data%20Providers%20\(SSRS\).md)   
 [Extensions &#40;SSRS&#41;](../Topic/Extensions%20\(SSRS\).md)  
  
  