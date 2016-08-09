---
title: "Data Source Properties Dialog Box, Credentials"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14c3eeb6-d37b-4fda-967b-43afcdb48119
caps.latest.revision: 40
manager: mblythe
---
# Data Source Properties Dialog Box, Credentials
Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to a data source in the report. The credentials that you provide are used to access the data source and to cache a copy of the data for previewing reports. For more information about how preview data is cached, see [Previewing Reports](../../Topics/TopicNameNotContainA/Previewing-Reports.md). For more information about credentials, see [Specify Credential and Connection Information for Report Data Sources](../../Topics/TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md).  
  
## Options  
 **Use Windows Authentication (integrated security)**  
 Select this option to use Windows Authentication.  
  
 **Use this user name and password**  
 Select this option to provide a specific user name and password. For shared data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database. If you want to use the user name and password as Windows credentials, you can edit the properties for the published shared data source on the target server. For more information, see [Create, Delete, or Modify a Shared Data Source (Report Manager)](../../Topics/TopicNameContainA/Create--Delete--or-Modify-a-Shared-Data-Source--Report-Manager-.md).  
  
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
 [Data Source Properties Dialog Box, General](../../Topics/TopicNameNotContainA/Data-Source-Properties-Dialog-Box--General.md)   
 [Specify Credential and Connection Information for Report Data Sources](../../Topics/TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)   
 [Data Connections, Data Sources, and Connection Strings (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings--Report-Builder-and-SSRS-.md)