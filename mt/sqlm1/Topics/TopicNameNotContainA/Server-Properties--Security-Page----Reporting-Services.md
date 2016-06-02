---
title: Server Properties (Security Page) - Reporting Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
---
# Server Properties (Security Page) - Reporting Services
  Use this page to turn off features that can potentially compromise a report server. Turning off these features will limit some functionality, but can improve the overall security of the report server by mitigating specific threats.  
  
 To open this page, start [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to a report server instance, right\-click the report server name, and select **Properties**. Click **Security** to open this page.  
  
## Options  
 **Enable Windows integrated security for report data sources**  
 Specify whether a connection to a report data source can be made using the Windows security token of the user who requested the report.  
  
 If you turn off this feature, the Windows Integrated Security feature in the report data source property pages will be unavailable. If report data sources are configured for Windows integrated security and you subsequently turn off this feature, the report server will immediately update all data source connection properties to prompt for credentials.  
  
 **Enable Ad Hoc Reporting**  
 Specify whether users can perform ad hoc queries from a Report Builder report, where new reports are automatically generated when a user clicks data of interest.  
  
 Setting this option determines whether the **EnableLoadReportDefinition** property on the report server is set to **True** or **False**. If you clear this option, the property will be set to **False** and report server will not generate clickthrough reports that are created during data exploration. All calls to the **LoadReportDefinition** method will be blocked.  
  
 Turning off this option mitigates a threat whereby a malicious user launches a denial of service attack by overloading the report server with **LoadReportDefinition** requests.  
  
## See Also  
 [Set Report Server Properties &#40;Management Studio&#41;](../Topic/Set%20Report%20Server%20Properties%20\(Management%20Studio\).md)   
 [Connect to a Report Server in Management Studio](../../Topics\TopicNameContainA/Connect-to-a-Report-Server-in-Management-Studio.md)   
 [Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)   
 [Report Server in Management Studio F1 Help](../../Topics\TopicNameNotContainA/Report-Server-in-Management-Studio-F1-Help.md)  
  
  