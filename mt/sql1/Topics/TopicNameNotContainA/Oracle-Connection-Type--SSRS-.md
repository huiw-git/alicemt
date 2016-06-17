---
title: Oracle Connection Type (SSRS)
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
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
---
# Oracle Connection Type (SSRS)
  To use data from an Oracle database in your report, you must you must have a dataset that is based on a report data source of type Oracle. This built\-in data source type is based on the .NET Framework Managed Provider for Oracle and requires an Oracle client software component.  
  
 Use the information in this topic to build a data source. For step\-by\-step instructions, see [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-and-Verify-a-Data-Connection--Report-Builder-and-SSRS-.md).  
  
##  <a name="Connection"></a> Connection String  
 Contact your database administrator for connection information and for the credentials to use to connect to the data source. The following connection string example specifies an Oracle database on the server named "Oracle9" using Unicode. The server name must match what is defined in the Tnsnames.ora configuration file as the Oracle server instance name.  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings-in-Report-Builder.md).  
  
##  <a name="Credentials"></a> Credentials  
 Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.  
  
 After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.  
  
 For more information, see [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings--Report-Builder-and-SSRS-.md) or [Specify Credentials in Report Builder](../../Topics/TopicNameNotContainA/Specify-Credentials-in-Report-Builder.md).  
  
 ![Arrow icon used with Back to Top link](../../Images/Image/ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Query"></a> Queries  
 To create a dataset, you can either select a stored procedure from a drop\-down list or create an SQL query. To build a query, you must use the text\-based query designer. For more information, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](../../Topics/TopicNameNotContainA/Text-based-Query-Designer-User-Interface--Report-Builder-.md).  
  
 You can specify stored procedures that return only one result set. Using cursor\-based queries are not supported.  
  
##  <a name="Parameters"></a> Parameters  
 If the query includes query variables, corresponding report parameters are automatically generated. Named parameters are supported by this extension. For Oracle version 9 or later, multivalue parameters are supported.  
  
 Report parameters are created with default property values that you might need to modify. For example, each report parameter is data type **Text**. After the report parameters are created, you might have to change default values. For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md).  
  
 ![Arrow icon used with Back to Top link](../../Images/Image/ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Remarks"></a> Remarks  
 Before you can connect an Oracle data source, the system administrator must have installed the version of the .NET Data Provider for Oracle that supports retrieving data from the Oracle database. This data provider must be installed on the same computer as Report Builder and also on the report server.  
  
 For more information, see the following:  
  
-   [Using the .NET Framework Data Provider for Oracle](http://go.microsoft.com/fwlink/?LinkId=112314) on msdn.microsoft.com  
  
-   [How to use Reporting Services to configure and to access an Oracle data source](http://support.microsoft.com/kb/834305)  
  
-   [How to add permissions for the NETWORK SERVICE security principal](http://support.microsoft.com/kb/870668)  
  
###### Alternate Data Extensions  
 You can also retrieve data from an Oracle database by using an OLE DB data source type. For more information, see [OLE DB Connection Type &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/OLE-DB-Connection-Type--SSRS-.md).  
  
###### Report Models  
 You can also create models based on an Oracle database.  
  
###### Platform and Version Information  
 For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Data-Sources-Supported-by-Reporting-Services--SSRS-.md) in the [!INCLUDE[ssRSnoversion](../../Token/Other/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
  
 ![Arrow icon used with Back to Top link](../../Images/Image/ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="HowTo"></a> How\-To Topics  
 This section contains step\-by\-step instructions for working with data connections, data sources, and datasets.  
  
 [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-and-Verify-a-Data-Connection--Report-Builder-and-SSRS-.md)  
  
 [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Create-a-Shared-Dataset-or-Embedded-Dataset--Report-Builder-and-SSRS-.md)  
  
 [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-a-Filter-to-a-Dataset--Report-Builder-and-SSRS-.md)  
  
 ![Arrow icon used with Back to Top link](../../Images/Image/ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="Related"></a> Related Sections  
 These sections of the documentation provide in\-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.  
  
 [Report Datasets &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md)  
 Provides an overview of accessing data for your report.  
  
 [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings-in-Report-Builder.md)  
 Provides information about data connections and data sources.  
  
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Report-Embedded-Datasets-and-Shared-Datasets--Report-Builder-and-SSRS-.md)  
 Provides information about embedded and shared datasets.  
  
 [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Dataset-Fields-Collection--Report-Builder-and-SSRS-.md)  
 Provides information about the dataset field collection generated by the query.  
  
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Data-Sources-Supported-by-Reporting-Services--SSRS-.md) in the [!INCLUDE[ssRSnoversion](../../Token/Other/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
 Provides in\-depth information about platform and version support for each data extension.  
  
 ![Arrow icon used with Back to Top link](../../Images/Image/ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
## See Also  
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md)   
 [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Filter--Group--and-Sort-Data--Report-Builder-and-SSRS-.md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md)  
  
  