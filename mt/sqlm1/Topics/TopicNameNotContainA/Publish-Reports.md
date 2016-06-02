---
title: Publish Reports
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
---
# Publish Reports
  From[!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], you can publish either all the reports and shared data sources in a Report Server project to a report server by deploying the project, or you can publish a single report. Before you can publish a report you must specify the URL of the target report server. For more information, see [Set Deployment Properties &#40;Reporting Services&#41;](../Topic/Set%20Deployment%20Properties%20\(Reporting%20Services\).md).  
  
 You can use the [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] version of [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to open, modify, preview, save, and publish both [!INCLUDE[ssRSversion2005](../../Token\Other/ssRSversion2005_md.md)] and [!INCLUDE[ssRSversion10](../../Token\Other/ssRSversion10_md.md)] reports. For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../Topic/Deployment%20and%20Version%20Support%20in%20SQL%20Server%20Data%20Tools%20\(SSRS\).md).  
  
### To publish all reports in a project  
  
-   On the **Build** menu, click **Deploy \<report project name\>**. Alternatively, in Solution Explorer, right\-click the report project and then click **Deploy**. You can view the status of the publishing process in the Output window.  
  
    > [!NOTE]  
    >  When you deploy a Report Server project, the shared data sources in the report project are also deployed.  
  
### To publish a single report  
  
-   In Solution Explorer, right\-click the report and then click **Deploy**. You can view the status of the publishing process in the Output window.  
  
    > [!NOTE]  
    >  When you publish a report, you must also deploy the shared data sources that the report uses.  
  
## See Also  
 [Publishing Data Sources and Reports](../../Topics\TopicNameNotContainA/Publishing-Data-Sources-and-Reports.md)   
 [Previewing Reports](../../Topics\TopicNameNotContainA/Previewing-Reports.md)   
 [Publishing Reports to a Report Server](../../Topics\TopicNameContainA/Publishing-Reports-to-a-Report-Server.md)   
 [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../Topic/Finding,%20Viewing,%20and%20Managing%20Reports%20\(Report%20Builder%20and%20SSRS%20\).md)   
 [Export Reports &#40;Report Builder and SSRS&#41;](../Topic/Export%20Reports%20\(Report%20Builder%20and%20SSRS\).md)  
  
  