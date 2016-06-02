---
title: Hyperion Essbase Connection Type (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 108a00b6-799f-4066-b796-da59e95c09fd
---
# Hyperion Essbase Connection Type (SSRS)
  To include data from a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] external data source in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)]. This built\-in data source type is based on the data extension for [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)], which enables you to retrieve multidimensional data from a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] external data source.  
  
 Use the information in this topic to build a data source. For step\-by\-step instructions, see [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../Topic/Add%20and%20Verify%20a%20Data%20Connection%20\(Report%20Builder%20and%20SSRS\).md).  
  
##  <a name="Connection"></a> Connection String  
 The following connection string example specifies a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data source on a server that uses port 13080 and XML for [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] \(XMLA\) over the Internet using SOAP, connecting to a sample catalog:  
  
```  
Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample  
```  
  
 For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics\TopicNameNotContainA/Data-Connections,-Data-Sources,-and-Connection-Strings-in-Report-Builder.md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Credentials"></a> Credentials  
 Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.  
  
 After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.  
  
 For more information, see [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md) or [Specify Credentials in Report Builder](../../Topics\TopicNameNotContainA/Specify-Credentials-in-Report-Builder.md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Query"></a> Queries  
 You can specify a query in the following ways:  
  
-   Build a query interactively. Use the graphical query designer in Design or Query mode to browse the metadata on the external data source and generate a query in Multidimensional Expression \(MDX\) syntax.  
  
    -   **Design View** Drag dimensions, members, member properties, measures, and KPIs from the metadata browser to the **Data** pane to build an MDX query. Drag calculated members from the CalculatedMembers pane to the Data pane to define additional dataset fields.  
  
    -   **Query View** Drag dimensions, members, member properties, measures, and KPIs from the metadata browser to the Query pane to build an MDX query. You can edit MDX text directly in the Query pane. Drag calculated members from the CalculatedMembers pane to the Query pane to define additional dataset fields.  
  
     For more information, see [Hyperion Essbase Query Designer User Interface &#40;Report Builder&#41;](../Topic/Hyperion%20Essbase%20Query%20Designer%20User%20Interface%20\(Report%20Builder\).md).  
  
-   Import an existing MDX query from a report. Use the **Import** query button to browse to an .rdl file and import a query. You can import a query from a report that contains an embedded dataset that is based on a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data source. Importing an MDX query directly from an .mdx file is not supported.  
  
 At design time, run the query to view a result set. After you build the query, view the dataset field collection that is generated from the metadata in the Report Data pane. When the report runs, the actual data is returned from the external data source.  
  
 The [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data processing extension supports extended dataset field properties. These are values that are available from the external data source but that do not appear in the Report Data pane. For more information, see [Extended Field Properties](#Extended) later in this topic.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Parameters"></a> To include query parameters, create a filter in the filter area in the query designer, and mark the filter as a parameter. For each filter, a dataset is automatically created to provide the available values. By default, these datasets do not appear in the Report Data pane. For more information, see [Show Hidden Datasets for Parameter Values for Multidimensional Data &#40;Report Builder and SSRS&#41;](../Topic/Show%20Hidden%20Datasets%20for%20Parameter%20Values%20for%20Multidimensional%20Data%20\(Report%20Builder%20and%20SSRS\).md).  
  
 By default, each report parameter has data type **Text**. After the report parameters are created, you might have to change default values. For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Extended"></a> Extended Field Properties  
 The [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data processing extension supports extended field properties. Extended field properties are properties in addition to **Value** and **IsMissing** that are defined for a dataset field by the data processing extension. Extended properties include predefined properties and custom properties. Predefined properties are properties common to multiple data sources. Custom properties are unique to each data source.  
  
 Extended field properties do not appear in the Report Data pane as items that you can drag onto your report layout. Instead, you drag the parent field of the property onto the report and then change the default property from **Value** to the property you want to use.  
  
 The name for an extended field property appears in the ToolTip when you rest the mouse on a field in the Metadata pane in the query designer. For more information about the query designer you can use to explore the underlying data, see [Hyperion Essbase Query Designer User Interface](../../Topics\TopicNameNotContainA/Hyperion-Essbase-Query-Designer-User-Interface.md).  
  
> [!NOTE]  
>  Values exist for extended field properties only if they are included in the MDX expression and the data source provides these values when your report runs and retrieves the data for its datasets. You can then refer to those **Field** property values from any expression using the syntax described in the following section. However, because these fields are specific to this data provider and not part of the report definition language, changes that you make to these values are not saved with the report definition.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
### Predefined Field Properties  
 Predefined field properties that are typically supported by multiple data providers and that appear in the underlying MDX query for a report dataset. For example, the MDX dimension property MEMBER\_UNIQUE\_NAME is mapped to the predefined report dataset field property **UniqueName**. To include the unique name value in a text box, use the expression `=Fields!`*\<FieldName\>*`.UniqueName`.  
  
 The following table provides a list of predefined field properties that you can use for a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data source.  
  
|**Property**|**Type**|**Description or expected value**|  
|------------------|--------------|---------------------------------------|  
|**Value**|**Object**|Specifies the data value of the field.<br /><br /> For a dimension property, this is mapped to MEMBER\_CAPTION. For a measure, this is mapped to the data value.|  
|**IsMissing**|**Boolean**|Indicates whether the field was found in the resulting data set.|  
|**FormattedValue**|**String**|Returns a formatted value for a key figure.<br /><br /> Mapped from FORMATTED\_VALUE in the MDX expression.|  
|**BackgroundColor**|**String**|Returns the background color defined in the database for the field.<br /><br /> Mapped from BACK\_COLOR in the MDX expression.|  
|**Color**|**String**|Returns the foreground color defined in the database for the item.<br /><br /> Mapped from FORE\_COLOR in the MDX expression.|  
|**UniqueName**|**String**|Returns the fully qualified name of a level.<br /><br /> Mapped from MEMBER\_UNIQUE\_NAME in the MDX expression.|  
  
 For more information about how to use fields and field properties in an expression, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Built-in%20Collections%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
### Custom Properties  
 Custom field properties that are supported by a data provider and that appear in the underlying MDX query for a report dataset, but do not appear in the report Datasets pane as fields under that dataset. For example, **Long Names** is a member property defined for a dimension level. To include the value in a text box, you use the expression `=Fields!`*\<FieldName\>*`("Long Names")`. Field names in the expression are case\-sensitive.  
  
 Use the following syntax to refer to custom extended properties in an expression:  
  
-   *Fields\!FieldName\("PropertyName"\)*  
  
 The following table shows the custom field property that you can use for a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data source.  
  
|**Property**|**Type**|**Description or expected value**|  
|------------------|--------------|---------------------------------------|  
|**FORMAT\_STRING**|**String**|Defined on a measure, this is the **FormattedValue** available as a String type.|  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Remarks"></a> Remarks  
 Not all report delivery modes are supported by this data provider. Delivering reports through data\-driven subscriptions is not supported for this data processing extension. For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../Topic/Use%20an%20External%20Data%20Source%20for%20Subscriber%20Data%20\(Data-Driven%20Subscription\).md) in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
  
 For more information, see [Using SQL Server 2005 Reporting Services with Hyperion Essbase](http://go.microsoft.com/fwlink/?LinkId=81970).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="HowTo"></a> How\-To Topics  
 This section contains step\-by\-step instructions for working with data connections, data sources, and datasets:  
  
 [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../Topic/Add%20and%20Verify%20a%20Data%20Connection%20\(Report%20Builder%20and%20SSRS\).md)  
  
 [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../Topic/Create%20a%20Shared%20Dataset%20or%20Embedded%20Dataset%20\(Report%20Builder%20and%20SSRS\).md)  
  
 [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Filter%20to%20a%20Dataset%20\(Report%20Builder%20and%20SSRS\).md)  
  
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
 Provides information about the field collection that is generated by the dataset query.  
  
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md) in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
 Provides in\-depth information about platform and version support for each data extension.  
  
 [Using SQL Server 2005 Reporting Services with Hyperion Essbase](http://go.microsoft.com/fwlink/?LinkId=81970)  
 Provides detailed information about working with this data extension.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
## See Also  
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md)   
 [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../Topic/Filter,%20Group,%20and%20Sort%20Data%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)  
  
  