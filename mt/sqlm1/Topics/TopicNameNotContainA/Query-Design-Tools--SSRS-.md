---
title: Query Design Tools (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8139a9d-4aeb-4e64-96f3-564edf60479f
---
# Query Design Tools (SSRS)
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides a variety of query design tools that you can use to create dataset queries in Report Designer. Some query designers provide alternate modes so that you can choose whether to work in visual mode or directly in the query language. This topic introduces each tool and describes the type of data source each one supports. The following tools are described in this topic:  
  
-   [Text\-based Query Designer](#Textbased)  
  
-   [Graphical Query Designer](#Graphical)  
  
-   [Report Model Query Designer](#Model)  
  
-   [MDX Query Designer](#MDX)  
  
-   [DMX Query Designer](#DMX)  
  
-   [SapNetWeaver BI Query Designer](#SAPBW)  
  
-   [Hyperion Essbase Query Designer](#Hyperion)  
  
 All of the query design tools run in the data design environment of [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] when you work with a Report Server project template or Report Server Wizard project template. For more information about working with the query designers, see [Reporting Services Query Designers](../../Topics\TopicNameNotContainA/Reporting-Services-Query-Designers.md).  
  
 The type of data source that you are working with determines the availability of a particular query designer.  
  
 The data source types that are available in your report are determined by the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] data extensions installed on your client or report server. For more information, see [RSReportDesigner Configuration File](../../Topics\TopicNameNotContainA/RSReportDesigner-Configuration-File.md) and [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md).  
  
 A data processing extension and its associated query designer can differ in support for data sources in the following ways:  
  
-   **By query designer type.** For example, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data source supports both the graphical and text\-based query designers.  
  
-   **By query language variation.** For example, a query language such as [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] can differ in syntax depending on the data source type. The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] language and the Oracle SQL language have some variation in syntax for a query command.  
  
-   **By support for the schema part of a database object name.** When a data source uses schemas as part of the database object identifier, the schema name must be supplied as part of the query for any names that do not use the default schema. For example, `SELECT FirstName, LastName FROM [Person].[Person]`.  
  
-   **By support for query parameters.** Data providers differ in support for parameters. Some data providers support named parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`. Some data providers support unnamed parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`. The parameter identifier might differ by data provider; for example, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses the "at" \(@\) symbol, Oracle uses the colon \(:\). Some data providers do not support parameters.  
  
-   **By ability to import queries.** For example, for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data source, you can import a query from a report definition file \(.rdl\) or from a .sql file.  
  
##  <a name="Textbased"></a> Text\-based Query Designer  
 The text\-based query designer is the default query building tool for most supported relational data sources, including [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], Oracle, Teradata, OLE DB, XML, and ODBC. In contrast with the graphical query designer, this query design tool does not validate query syntax during query design. The following image provides an illustration of the text\-based query designer.  
  
 ![Generic query designer, for relational data query](../../Images\Image\ImageNotContaina/rsQD_DSAW_SQL_Generic.gif "rsQD_DSAW_SQL_Generic")  
  
 The text\-based query designer is recommended for creating complex queries, using stored procedures, querying XML data, and for writing dynamic queries. Depending on the data source, you may be able to toggle the **Edit As Text** button on the toolbar to switch between the graphical query designer and the text\-based query designer. For more information, see [Text-based Query Designer User Interface](../../Topics\TopicNameNotContainA/Text-based-Query-Designer-User-Interface.md).  
  
##  <a name="Graphical"></a> Graphical Query Designer  
 The graphical query designer is used to create or modify [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries that run against a relational database. This query design tool is used in several [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] products and in other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components. Depending on the data source type, it supports Text, StoredProcedure, and TableDirect modes. The following image provides an illustration of the graphical query designer.  
  
 ![Graphical query designer for sql query](../../Images\Image\ImageNotContaina/rsQD_DSAW_SQL.gif "rsQD_DSAW_SQL")  
  
 You can toggle the **Edit As Text** button on the toolbar to switch between the graphical query designer and the text\-based query designer. For more information, see [Graphical Query Designer User Interface](../../Topics\TopicNameNotContainA/Graphical-Query-Designer-User-Interface.md).  
  
##  <a name="Model"></a> Report Model Query Designer  
 The Report Model query designer is used to create or modify queries that run against a SMDL report model that has been published to a report server. Reports that run against models support clickthrough data exploration. The query determines the path of data exploration at run time. The following image provides an illustration of the Report Model query designer.  
  
 ![Semantic Model Query Designer UI](../../Images\Image\ImageNotContaina/rsQD_DSAWModel_SMQL.gif "rsQD_DSAWModel_SMQL")  
  
 To use the Report Model query designer, you must define a data source that points to a published model. When you define a dataset for the data source, you can open the dataset query in the Report Model query designer. The Report Model query designer can be used in graphical or text\-based modes. You can toggle the **Edit As Text** button on the toolbar to switch between the graphical query designer and the text\-based query designer. For more information, see [Report Model Query Designer User Interface](../../Topics\TopicNameNotContainA/Report-Model-Query-Designer-User-Interface.md).  
  
##  <a name="MDX"></a> MDX Query Designer  
 The Multidimensional Expression \(MDX\) query designer is used to create or modify queries that run against an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data source with multidimensional cubes. The following image provides an illustration of the MDX query designer after the query and filter are defined.  
  
 ![Analysis Services MDX query designer, design view](../../Images\Image\ImageNotContaina/rsQD_DSAWAS_MDX_DesignMode.gif "rsQD_DSAWAS_MDX_DesignMode")  
  
 To use the MDX query designer, you must define a data source that has an Analysis Services cube available that is valid and has been processed. When you define a dataset for the data source, you can open the query in the MDX query designer. If necessary, use the MDX and DMX buttons on the toolbar to switch between MDX and DMX modes. For more information, see [Analysis Services MDX Query Designer User Interface](../../Topics\TopicNameNotContainA/Analysis-Services-MDX-Query-Designer-User-Interface.md).  
  
##  <a name="DMX"></a> DMX Query Designer  
 The Data Mining Prediction Expression \(DMX\) query designer is used to create or modify queries that run against an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data source with mining models. The following image provides an illustration of the DMX query designer after the model and input tables are selected.  
  
 ![Analysis Services DMX query designer, design view](../../Images\Image\ImageNotContaina/rsQD_DSAWAS_DMX_DesignMode.gif "rsQD_DSAWAS_DMX_DesignMode")  
  
 To use the DMX query designer, you must define a data source that has a valid, data mining model available. When you define a dataset for the data source, you can open the query in the DMX query designer. If necessary, use the MDX and DMX buttons on the toolbar to switch between MDX and DMX modes. After you select the model, you can create data mining prediction queries that provide data to a report. For more information, see [Analysis Services DMX Query Designer User Interface](../../Topics\TopicNameNotContainA/Analysis-Services-DMX-Query-Designer-User-Interface.md).  
  
##  <a name="SAPBW"></a> Sap NetWeaver BI Query Designer  
 The [!INCLUDE[SAP_DPE_BW_1](../../Token\Other/SAP_DPE_BW_1_md.md)] query designer is used to retrieve data from a [!INCLUDE[SAP_DPE_BW_1](../../Token\Other/SAP_DPE_BW_1_md.md)] database. To use this query designer, you must have an [!INCLUDE[SAP_DPE_BW_1](../../Token\Other/SAP_DPE_BW_1_md.md)] data source that has at least one InfoCube, MultiProvider, or Web\-enabled query defined. The following image provides an illustration of the [!INCLUDE[SAP_DPE_BW_1](../../Token\Other/SAP_DPE_BW_1_md.md)] query designer. For more information, see [SAP NetWeaver BI Query Designer User Interface](../../Topics\TopicNameNotContainA/SAP-NetWeaver-BI-Query-Designer-User-Interface.md).  
  
 ![Query Designer using MDX in Design Mode](../../Images\Image\ImageNotContaina/rsQD_DSSAPBW_MDX_DesignMode.gif "rsQD_DSSAPBW_MDX_DesignMode")  
  
##  <a name="Hyperion"></a> Hyperion Essbase Query Designer  
 The [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] query designer is used to retrieve data from [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] databases and applications. The following image provides an illustration of the [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] query designer.  
  
 ![Query Designer for Hyperion Essbase data source](../../Images\Image\ImageNotContaina/rsQD_DSHyperionEssbase_MDX_DesignMode.gif "rsQD_DSHyperionEssbase_MDX_DesignMode")  
  
 To use this query designer, you must have a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data source that has at least one database.  
  
 For more information, see [Hyperion Essbase Query Designer User Interface](../../Topics\TopicNameNotContainA/Hyperion-Essbase-Query-Designer-User-Interface.md).  
  
## See Also  
 [Reporting Services Tools](../../Topics\TopicNameNotContainA/Reporting-Services-Tools.md)   
 [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md)   
 [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)   
 [Reporting Services Tutorials &#40;SSRS&#41;](../Topic/Reporting%20Services%20Tutorials%20\(SSRS\).md)   
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md)   
 [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../Topic/Create%20an%20Embedded%20or%20Shared%20Data%20Source%20\(SSRS\).md)  
  
  