---
title: Specify Credentials in Report Builder
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7412ce68-aece-41c0-8c37-76a0e54b6b53
robots: noindex,nofollow
---
# Specify Credentials in Report Builder
  Credentials authenticate the user who is attempting to retrieve data from a source of data. The owner of the source of data determines the type of credentials that must be used. For example, a database administrator might specify that the user must provide a Windows username and password.  
  
 In a report definition, each data source definition specifies a name, a connection string, whether to use integrated security, and what prompt to display if credentials are required but not specified. Credentials are not saved in the report definition. After a report is published on the report server, data sources can be managed independently from a report definition. Data source owners can specify credentials for both embedded and shared data sources on the report server.  
  
> [!NOTE]  
>  The report server administrator must grant a user the appropriate permissions to browse the report server to select shared data sources or models or to open or save reports. For more information, see [Install and Uninstall Report Builder](../../Topics\TopicNameNotContainA/Install-and-Uninstall-Report-Builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Understanding When Credentials are Used  
 In Report Builder, credentials are often used when you connect to a report server or for data\-related tasks, such as creating an embedded data source, running a dataset query, or previewing a report. Credentials are not stored in the report. They are managed separately on the report server or on the local client. The following list describes the types of credentials that you might need to provide, where they are stored, and how they are used:  
  
-   Report server credentials that you enter in the [Reporting Services Login Dialog Box &#40;Report Builder&#41;](../Topic/Reporting%20Services%20Login%20Dialog%20Box%20\(Report%20Builder\).md).  
  
     When you first save to, publish to, or browse to a report server or SharePoint site, you might need to enter your credentials. The credentials that you enter are used until the Report Builder session ends. If you choose to save the credentials, they are stored securely with your user settings on your computer. In subsequent Report Builder sessions, saved credentials are used to connect to the same report server or SharePoint site. The report server administrator or SharePoint administrator specifies which type of credentials to use.  
  
-   Data source credentials that you enter in the [Data Source Properties Dialog Box, Credentials &#40;Report Builder&#41;](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20Credentials%20\(Report%20Builder\).md) page for an embedded data source.  
  
     These credentials are used by the report server to make a data connection to the external data source. For some types of data sources, credentials can be stored securely on the report server. These credentials enable other users to run the report without providing credentials for the underlying data connection.  
  
-   Data source credentials that you enter in the [Enter Data Source Credentials Dialog Box &#40;Report Builder&#41;](../Topic/Enter%20Data%20Source%20Credentials%20Dialog%20Box%20\(Report%20Builder\).md) when you run a dataset query, refresh dataset fields, or preview the report.  
  
     These credentials are used to make a data connection from Report Builder to the external data source, or to preview a report that is configured to prompt for credentials. Credentials that you enter in this dialog box are not stored on the report server and are not available for use by other users. Report Builder caches the credentials during the report editing session so that you do not need to enter them every time you run the query or preview the report.  
  
     For shared data sources, use the **Save my password** option to save the credentials locally with your user settings on your computer. Report Builder uses the saved credentials every time a connection is made to the corresponding external data source.  
  
 For more information, see [Data Source Properties Dialog Box, General &#40;Report Builder&#41;](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder\).md) and [Previewing Reports in Report Builder](../../Topics\TopicNameNotContainA/Previewing-Reports-in-Report-Builder.md).  
  
## Types of Credentials  
 The type of credentials that a data source supports is specified by the owner of the data source. For example, to access a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database, you might need to provide a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login user name and password. To access a different data source, you might need to provide a Windows user name and password. Some data sources might not require credentials.  
  
### Options for Specifying Credentials  
 The following options are available to specify credentials for a data source:  
  
-   Use the current Windows user \(also known as integrated security\).  
  
-   Use a stored user name and password.  
  
-   Prompt the user for credentials.  
  
-   No credentials are required.  
  
### Windows Integrated Security  
 When you select **Use Windows Authentication \(integrated security\)**, the security token of the current user is passed to the data source. In this case, the user is not prompted to type a user name or password. This option usually requires that delegation features are enabled. If these features are not enabled, you can only use this option to access a data source that is located on the same computer.  
  
### User Name and Password Login  
 When you select **Use this user name and password**, a user name and password must be supplied to access the data source. For a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database, the credentials might be for a database login. The credentials are passed to the data source for authentication.  
  
### Prompted Credentials  
 When you specify prompted credentials, each user who accesses the report must enter a user name and password to retrieve the data. This option is recommended for reports that contain confidential data. Prompted credentials can be for a Windows account or a database login. If the database server does not recognize the credentials that you provide, or if the specified user does not has not been granted permission to retrieve the data, the connection fails.  
  
### No Credentials  
 Credentials are not required for this data source. To run this report on the report server, the unattended execution account must be configured. For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Unattended%20Execution%20Account%20\(SSRS%20Configuration%20Manager\).md) in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
  
## See Also  
 [Install and Uninstall Report Builder](../../Topics\TopicNameNotContainA/Install-and-Uninstall-Report-Builder.md)   
 [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../Topic/Embedded%20and%20Shared%20Data%20Connections%20or%20Data%20Sources%20\(Report%20Builder%20and%20SSRS\).md)   
 [Set default options for Report Builder](../../Topics\TopicNameNotContainA/Set-default-options-for-Report-Builder.md)   
 [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics\TopicNameNotContainA/Data-Connections,-Data-Sources,-and-Connection-Strings-in-Report-Builder.md)   
 [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md)   
 [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../Topic/Add%20and%20Verify%20a%20Data%20Connection%20\(Report%20Builder%20and%20SSRS\).md)  
  
  