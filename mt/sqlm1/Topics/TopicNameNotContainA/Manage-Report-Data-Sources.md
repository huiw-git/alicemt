---
title: Manage Report Data Sources
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0475aded-c8fe-4337-a2b5-4df0ec4c46af
---
# Manage Report Data Sources
  In [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], reports, report models, and data\-driven subscriptions retrieve data from external data sources. To connect to an external data source, a report server uses data source connection information that is defined in or referenced from the report, model, or subscription. Data source connection properties are always defined with the report or model when you create it, but can be independently managed after the report or model is published to a report server.  
  
 To manage report data sources, you can use Report Manager for a native mode report server or application pages on a SharePoint site if you deployed the report server in SharePoint integrated mode.  
  
 Managing data source connections are characterized by the following tasks, which are described in this topic:  
  
-   Changing connection strings.  
  
-   Changing credentials.  
  
-   Creating and using shared data sources on a report server, including switching an embedded data source for a shared data source.  
  
-   Controlling access to data source properties by setting permissions on the report, model, or any shared data sources you are using.  
  
 Notice that modifying queries is not part of data source connection management. To modify a query for a report or model, you must use an authoring tool and make your changes in the report or model definition.  
  
## Managed Properties: Data Source Type, Connection Strings, and Credentials  
 Data source properties that you can manage on a report server are:  
  
|Property|Description|How to manage it|  
|--------------|-----------------|----------------------|  
|Data source type|Determines which report server data processing extension to use on the external data. Examples of data processors include SQL Server, Analysis Services, and Oracle.|The data source type is a managed property because it is configurable. However, you should only configure a data source type if you are creating a new shared data source.<br /><br /> Do not change the data source type in the property pages of a published report or model, as doing so will almost certainly invalidate the connection. It is unlikely that the data structures required by a report or model will be identical on a different data platform.|  
|Connection string|Establishes the initial connection to an external data source. A report can use static or dynamic connection strings.<br /><br /> A *static connection string* is a set of values that the report always uses to connect to the same data source each time the report runs.<br /><br /> A *dynamic connection string* is an expression that you build into the report, allowing the user to select which data source to use at run time. You must build the expression and data source selection list into the report when you create it in Report Designer.|Changing a connection string is useful if you move a data source to another computer, or if you created reports using test data but you want to deploy the reports with a production database.<br /><br /> You can manage a static connection string by replacing the original string with a different one.<br /><br /> To manage a dynamic connection string in Report Manager or on a SharePoint site, you are limited to replacing it with a static one. You cannot edit the expression itself, nor change the data source selection list. To change the expression or valid values list, you must edit the report definition and republish it to the report server. For more information, see [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md).|  
|Credentials|Provides the name and password of a user who has permission to read data from the data source.<br /><br /> If a data source does not support authentication \(for example, if the data source is an XML file on the file system\), you can configure the unattended execution account to allow the report server to connect to the external data source without passing credentials.|You can manage credentials by updating the user account or a password if it expired.<br /><br /> You can also change the way credentials are obtained \(for example, prompting users to enter credentials at run time\).<br /><br /> If you want to users to be able to subscribe to a report, you must configure the report to use stored credentials.|  
  
## Creating and Using Shared Data Sources  
 If you publish a report with data source properties embedded in the report, consider switching to shared data source properties. Shared data sources are easier to manage because you can update credentials and connection strings in one page. All reports, models, and data\-driven subscriptions that use that data source pick up the changes immediately. You can also take a shared data source offline, effectively pausing the report or subscription to prevent it from executing while you troubleshoot or investigate any problems that arise.  
  
## Controlling Access Data Source Properties  
 By default, anyone who has permission to manage reports can set any property on the report, including properties that determine the data source type, connection string, credentials, and whether the report gets connection information from an embedded or a shared data source. For more information about which tasks and permissions control access to data source properties on a native mode report server, see [Secure Shared Data Source Items](../../Topics\TopicNameNotContainA/Secure-Shared-Data-Source-Items.md) and [Secure Reports and Resources](../../Topics\TopicNameNotContainA/Secure-Reports-and-Resources.md).  
  
 Permissions to view and edit properties for items in a SharePoint library are determined by the site administrator. For more information about which permissions control access to data source connection properties, see [SharePoint Site and List Permission Reference for Report Server Items](../../Topics\TopicNameNotContainA/SharePoint-Site-and-List-Permission-Reference-for-Report-Server-Items.md).  
  
## How to Work with Data Source Properties on a Report Server  
 You can use a variety of tools to create and modify data source properties. The following table summarizes the approaches and tools, and provides a link to additional instructions.  
  
|Task|Tool|Link|  
|----------|----------|----------|  
|View examples of connection strings.||[Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)|  
|Choose an approach for getting credentials to connect to a data source.||[Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)|  
|Add data source connection properties to a report definition \(.rdl\) file.|Report Designer|[Create an Embedded or Shared Data Source &#40;SSRS&#41;](../Topic/Create%20an%20Embedded%20or%20Shared%20Data%20Source%20\(SSRS\).md)|  
|Add and link to a shared data source \(.rds\) file in report project.|Report Designer|[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](../Topic/Create,%20Modify,%20and%20Delete%20Shared%20Data%20Sources%20\(SSRS\).md)|  
|Create a predefined list of data sources that users can select at run time. When a user requests a report, the report provides a list of data sources. The user must select which data source to use prior to running the report. To add a data source selection list to a report, you use an expression.<br /><br /> This is known as a dynamic data source connection.|Report Designer|[Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)|  
|Create a shared data source item on a report server.|Report Manager|[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)|  
|Store credentials as a prerequisite for creating subscriptions or report snapshots.|Report Manager|[Store Credentials in a Reporting Services Data Source](../../Topics\TopicNameContainA/Store-Credentials-in-a-Reporting-Services-Data-Source.md)|  
|Edit data source connection properties on a published report.|Report Manager|[Configure Data Source Properties for a Report  &#40;Report Manager&#41;](../Topic/Configure%20Data%20Source%20Properties%20for%20a%20Report%20%20\(Report%20Manager\).md)|  
|Create a shared data source item on a report server.|SharePoint site|[Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)|  
|Use existing .odc connection information with a report.|SharePoint site|[Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;](../Topic/Use%20an%20Office%20Data%20Connection%20\(.odc\)%20with%20Reports%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)|  
  
> [!NOTE]  
>  Managing data source connections to report data sources is not the same as managing the report server connection to the report server database. For more information about a report server connection to its internal data store, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md).  
  
## See Also  
 [Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](../Topic/Bind%20a%20Report%20or%20Model%20to%20a%20Shared%20Data%20Source%20\(SSRS\).md)   
 [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Store Credentials in a Reporting Services Data Source](../../Topics\TopicNameContainA/Store-Credentials-in-a-Reporting-Services-Data-Source.md)   
 [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md)   
 [Report Server Content Management &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Content%20Management%20\(SSRS%20Native%20Mode\).md)  
  
  