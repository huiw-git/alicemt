---
title: SAP NetWeaver BI Connection Type (SSRS)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
---
# SAP NetWeaver BI Connection Type (SSRS)
  To include data from a SAP NetWeaver® Business Intelligence external data source in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[SAP_DPE_BW_1](../../Topics/TopicNameNotContainA/includes/SAP_DPE_BW_1_md.md)]. This built-in data source type is based on the data extension for the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../Topics/TopicNameNotContainA/includes/SAP_DPE_BW_1_md.md)].  
  
 This data extension enables you to retrieve multidimensional data from InfoCubes, MultiProviders (virtual InfoCubes), and Web-enabled queries that are defined on a [!INCLUDE[SAP_DPE_BW_1](../../Topics/TopicNameNotContainA/includes/SAP_DPE_BW_1_md.md)] external data source.  
  
 Use the information in this topic to build a data source. For step-by-step instructions, see [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-and-Verify-a-Data-Connection--Report-Builder-and-SSRS-.md).  
  
##  <a name="Connection"></a> Connection String  
 Contact the database administrator for connection information and for the credentials to use to connect to the data source. The following connection string example specifies an [!INCLUDE[SAP_DPE_BW_1](../../Topics/TopicNameNotContainA/includes/SAP_DPE_BW_1_md.md)] data source on a server using port 8000 and XML for Analysis Services (XMLA) over the Internet using SOAP:  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings-in-Report-Builder.md).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Credentials"></a> Credentials  
 Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.  
  
 After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.  
  
 For more information, see [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings--Report-Builder-and-SSRS-.md) or [Specify Credentials in Report Builder](../../Topics/TopicNameNotContainA/Specify-Credentials-in-Report-Builder.md).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Query"></a> Queries  
 You can use the graphical query designer in Design or Query mode to build a Multidimensional Expression (MDX) query by browsing the underlying data structures on the data source. At design time, you can interactively run a query from the query designer to see the results. The query you build defines fields in the dataset. At run time, the actual data is returned from the data source. Use the graphical query designer to perform the following actions:  
  
-   In Design mode, drag dimensions, members, member properties, and key figures from the data source onto a Data pane to build a Multidimensional Expression (MDX) query. Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.  
  
-   In Query mode, drag dimensions, members, member properties, and key figures onto the Query pane or type MDX text directly into the Query pane. Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.  
  
 As you build queries, the query designer automatically adds default properties to the MDX query. To include properties other than default properties, you must manually modify the MDX query.  
  
 For more information about working with this query designer, see [SAP NetWeaver BI Query Designer User Interface &#40;Report Builder&#41;](../../Topics/TopicNameNotContainA/SAP-NetWeaver-BI-Query-Designer-User-Interface--Report-Builder-.md).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Extended"></a> Extended Field Properties  
 The [!INCLUDE[SAP_DPE_BW_1](../../Topics/TopicNameNotContainA/includes/SAP_DPE_BW_1_md.md)] data source supports extended field properties. Extended field properties are properties in addition to **Value** and **IsMissing** that are defined for a dataset field by the data processing extension. Extended properties include predefined properties and custom properties. Predefined properties are properties common to multiple data sources. Custom properties are unique to each data source.  
  
### Working with Field Properties  
 Extended field properties do not appear in the Report Data pane as items that you can drag onto your report layout. Instead, you drag the parent field of the property onto the report and then change the default property from **Value** to the property you want to use. For example, if the field name **Calendar Year/Month Level 01** is created in an MDX query designer by dropping a level from the Metadata pane onto the Query pane, you would refer to the custom extended property **Long Name** in an expression using the following syntax:  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 The name for an extended field property appears in the ToolTip when you hover over a field in the Metadata pane. For more information about the query designers you can use to explore the underlying data, see [SAP NetWeaver BI Query Designer User Interface](../../Topics/TopicNameNotContainA/SAP-NetWeaver-BI-Query-Designer-User-Interface.md).  
  
> [!NOTE]  
>  Values exist for extended field properties only if the data source provides these values when your report runs and retrieves the data for its datasets. You can then refer to those **Field** property values from any expression using the syntax described below. However, because these fields are specific to this data provider and not part of the report definition language, changes that you make to these values are not saved with the report definition.  
  
 Use either of the following syntaxes to refer to predefined extended properties in an expression:  
  
-   *Fields!FieldName.PropertyName*  
  
-   *Fields!FieldName("PropertyName")*  
  
 Use the following syntax to refer to custom extended properties in an expression:  
  
-   *Fields!FieldName("PropertyName")*  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
### Predefined Field Properties  
 The following table provides a list of predefined field properties that you can use for an [!INCLUDE[SAP_DPE_BW_1](../../Topics/TopicNameNotContainA/includes/SAP_DPE_BW_1_md.md)] data source.  
  
|**Property**|**Type**|**Description or expected value**|  
|------------------|--------------|---------------------------------------|  
|**Value**|**Object**|Specifies the data value of the field.|  
|**IsMissing**|**Boolean**|Indicates whether the field was found in the resulting data set.|  
|**FormattedValue**|**String**|Returns a formatted value for a key figure.|  
|**BackgroundColor**|**String**|Returns the background color defined in the database for the field.|  
|**Color**|**String**|Returns the foreground color defined in the database for the item.|  
|**Key**|**Object**|Returns the key for a level.|  
|**LevelNumber**|**Integer**|For parent-child hierarchies, returns the level or dimension number.|  
|**ParentUniqueName**|**String**|For parent-child hierarchies, returns a fully qualified name of the parent level.|  
|**UniqueName**|**String**|Returns the fully qualified name of a level. For example, the **UniqueName** value for an employee might be *[0D_Company].[10D_Department].[11]*.|  
  
 For more information about using fields and field properties in an expression, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Built-in-Collections-in-Expressions--Report-Builder-and-SSRS-.md).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Remarks"></a> Remarks  
 Not all report delivery modes are supported by this data provider. Delivering reports through data-driven subscriptions is not supported for this data processing extension. For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../../Topics/TopicNameNotContainA/Use-an-External-Data-Source-for-Subscriber-Data--Data-Driven-Subscription-.md).  
  
 For more information, see [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence](http://go.microsoft.com/fwlink/?LinkId=167352).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="HowTo"></a> How-To Topics  
 This section contains step-by-step instructions for working with data connections, data sources, and datasets.  
  
 [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-and-Verify-a-Data-Connection--Report-Builder-and-SSRS-.md)  
  
 [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Create-a-Shared-Dataset-or-Embedded-Dataset--Report-Builder-and-SSRS-.md)  
  
 [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-a-Filter-to-a-Dataset--Report-Builder-and-SSRS-.md)  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Related"></a> Related Sections  
 These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.  
  
 [Report Datasets &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md)  
 Provides an overview of accessing data for your report.  
  
 [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings-in-Report-Builder.md)  
 Provides information about data connections and data sources.  
  
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Report-Embedded-Datasets-and-Shared-Datasets--Report-Builder-and-SSRS-.md)  
 Provides information about embedded and shared datasets.  
  
 [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Dataset-Fields-Collection--Report-Builder-and-SSRS-.md)  
 Provides information about the dataset field collection generated by the query.  
  
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Data-Sources-Supported-by-Reporting-Services--SSRS-.md)  
 Provides in-depth information about platform and version support for each data extension.  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/media/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
## See Also  
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md)   
 [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Filter--Group--and-Sort-Data--Report-Builder-and-SSRS-.md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md)  
  
  