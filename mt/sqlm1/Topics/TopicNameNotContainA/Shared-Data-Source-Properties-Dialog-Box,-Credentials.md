---
title: Shared Data Source Properties Dialog Box, Credentials
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c08d1a5f-206b-4d53-ab1a-368b651ee5bb
---
# Shared Data Source Properties Dialog Box, Credentials
  Select **Credentials** on the **Shared Data Source Properties** dialog box to display and modify credentials to connect to a shared data source in the report. The credentials that you provide are used to access the data source and to cache a copy of the data for previewing reports. For more information about how preview data is cached, see [Previewing Reports](../../Topics\TopicNameNotContainA/Previewing-Reports.md). For more information about credentials, see [Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md).  
  
## Options  
 **Use Windows Authentication \(integrated security\)**  
 Select this option to use Windows Authentication.  
  
 **Use this user name and password**  
 Select this option to provide a specific user name and password. For shared data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database. If you want to use the user name and password as Windows credentials, you can edit the properties for the published shared data source on the target server. For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md).  
  
 **User name**  
 Type a user name to log in to the data source.  
  
 **Password**  
 Type a password to log in to the data source.  
  
 **Prompt for credentials**  
 Select this option to prompt for credentials when the report is run.  
  
 **Enter prompt string**  
 Type a sentence to instruct the user to provide login credentials for the data source.  
  
 **No credentials**  
 Select this option to provide no credentials for the data source. This option only works if the data source does not accept credentials or if you are passing credentials some other way.  
  
## See Also  
 [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)   
 [Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)   
 [Shared Data Source Properties Dialog Box, General](../../Topics\TopicNameNotContainA/Shared-Data-Source-Properties-Dialog-Box,-General.md)  
  
  