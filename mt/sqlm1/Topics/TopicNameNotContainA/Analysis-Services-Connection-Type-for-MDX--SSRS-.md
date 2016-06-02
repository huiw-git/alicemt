---
title: Analysis Services Connection Type for MDX (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd2e7148-3124-4e07-9734-22333127c3be
---
# Analysis Services Connection Type for MDX (SSRS)
  To include data from an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] cube in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. This built\-in data source type is based on the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data extension. You can retrieve metadata about dimensions, hierarchies, levels, key performance indicators \(KPIs\), measures, and attributes from a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] cube for use as report data.  
  
 This data processing extension supports multivalue parameters, server aggregates, and credentials that are managed separately from the connection string.  
  
 Use the information in this topic to build a data source. For step\-by\-step instructions, see [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../Topic/Add%20and%20Verify%20a%20Data%20Connection%20\(Report%20Builder%20and%20SSRS\).md).  
  
##  <a name="Connection"></a> Connection String  
 When you connect to a [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] cube, you are connecting to the database object in an Analysis Services instance on a server. The database might have multiple cubes. You specify the cube in the query designer when you build the query. The following example shows a connection string:  
  
```  
data source=<server name>;initial catalog=<database name>  
```  
  
 For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics\TopicNameNotContainA/Data-Connections,-Data-Sources,-and-Connection-Strings-in-Report-Builder.md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Credentials"></a> Credentials  
 Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.  
  
 After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.  
  
 From a report authoring client, the following options are available to specify credentials:  
  
-   Current Windows user \(also known as integrated security\).  
  
-   Use a stored user name and password.  
  
-   Prompt the user for credentials. This option only supports Windows integrated security.  
  
-   No credentials are required. To use this option, you must have the unattended execution account configured on the report server. For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Unattended%20Execution%20Account%20\(SSRS%20Configuration%20Manager\).md) in the [Reporting Services documentation](http://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.  
  
 For more information, see [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md) or [Specify Credentials in Report Builder](../../Topics\TopicNameNotContainA/Specify-Credentials-in-Report-Builder.md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Query"></a> Queries  
 After you have a data connection to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data source, you create a dataset and define a Multidimensional Expression \(MDX\) query that specifies which data to retrieve from the cube. Use the MDX graphical query designer browse and selecting from the underlying data structures on the data source.  
  
 You can specify a query in the following ways:  
  
-   Build a query interactively. The Analysis Services MDX Query Designer supports the following views:  
  
    -   **Design View** Drag dimensions, members, member properties, measures, and KPIs from the metadata browser to the **Data** pane to build an MDX query. Drag calculated members from the CalculatedMembers pane to the Data pane to define additional dataset fields.  
  
    -   **Query View** Drag dimensions, members, member properties, measures, and KPIs from the metadata browser to the Query pane to build an MDX query. You can edit MDX text directly in the Query pane. Drag calculated members from the CalculatedMembers pane to the Query pane to define additional dataset fields.  
  
     For more information, see [Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../Topic/Analysis%20Services%20MDX%20Query%20Designer%20User%20Interface%20\(Report%20Builder\).md).  
  
-   Import an existing MDX query from a report. Use the **Import** query button to browse to an .rdl file and import a query. You can import a query from a report that contains an embedded dataset that is based on a [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data source. Importing an MDX query directly from an .mdx file is not supported.  
  
 At design time, run the query to view a result set. The query results are automatically retrieved as a flattened rowset. The columns in the result set for a query populate the field collection for a dataset. After you build the query, view the dataset field collection that is generated from the metadata in the Report Data pane. When the report runs, the actual data is returned from the external data source.  
  
 The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data processing extension supports extended dataset field properties. These are values that are available from the external data source but that do not appear in the Report Data pane. You can use extended field properties supported by the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data processing extension in your report through the built\-in **Fields** collection. For properties that have values on the data source, you can access predefined property values such as **FormattedValue**, **Color**, or **UniqueName**. For more information, see [Extended Field Properties for an Analysis Services Database &#40;SSRS&#41;](../Topic/Extended%20Field%20Properties%20for%20an%20Analysis%20Services%20Database%20\(SSRS\).md)\).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Parameters"></a> Parameters  
 To include query parameters, create a filter in the filter area in the query designer, and mark the filter as a parameter. For each filter, a dataset is automatically created to provide the available values. By default, these datasets do not appear in the Report Data pane. For more information, see [Define Parameters in the MDX Query Designer for Analysis Services &#40;Report Builder and SSRS&#41;](../Topic/Define%20Parameters%20in%20the%20MDX%20Query%20Designer%20for%20Analysis%20Services%20\(Report%20Builder%20and%20SSRS\).md) and [Show Hidden Datasets for Parameter Values for Multidimensional Data &#40;Report Builder and SSRS&#41;](../Topic/Show%20Hidden%20Datasets%20for%20Parameter%20Values%20for%20Multidimensional%20Data%20\(Report%20Builder%20and%20SSRS\).md).  
  
 By default, each report parameter has data type **Text**. After the report parameters are created, you might have to change default values. For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Remarks"></a> Remarks  
 The Analysis Services data extension is based on the XMLA \(XML for Analysis\) protocol. Result sets from cubes are retrieved through the XMLA protocol as a flattened row set. Ragged hierarchies are not supported. For more information, see [Ragged Hierarchies](../../Topics\TopicNameNotContainA/Ragged-Hierarchies.md).  
  
 You can also retrieve data from an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] cube from the OLE DB data source type. For more information, see [OLE DB Connection Type &#40;SSRS&#41;](../Topic/OLE%20DB%20Connection%20Type%20\(SSRS\).md).  
  
 For more information about version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md) in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Related"></a> Related Sections  
 These sections of the documentation provide in\-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.  
  
 [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md)  
 Provides an overview of accessing data for your report.  
  
 [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics\TopicNameNotContainA/Data-Connections,-Data-Sources,-and-Connection-Strings-in-Report-Builder.md)  
 Provides information about data connections and data sources.  
  
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)  
 Provides information about embedded and shared datasets.  
  
 [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../Topic/Dataset%20Fields%20Collection%20\(Report%20Builder%20and%20SSRS\).md)  
 Provides information about the dataset field collection generated by the query.  
  
 [Extended Field Properties for an Analysis Services Database &#40;SSRS&#41;](../Topic/Extended%20Field%20Properties%20for%20an%20Analysis%20Services%20Database%20\(SSRS\).md)  
 Provides information about extra fields that are available through the XMLA data provider.  
  
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md) in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
 Provides in\-depth information about platform and version support for each data extension.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
## See Also  
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md)   
 [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../Topic/Filter,%20Group,%20and%20Sort%20Data%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)  
  
  