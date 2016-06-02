---
title: MHTML Device Information Settings
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
---
# MHTML Device Information Settings
  The following table lists the device information settings for rendering reports in Web archive \(MHTML\) format.  
  
|Setting|Value|  
|-------------|-----------|  
|**JavaScript**|Indicates whether JavaScript is supported in the rendered report.|  
|**OutlookCompat**|Indicates whether to render with extra metadata that makes the report look better in Outlook. The default value is **true**.|  
|**MHTML Fragment**|Indicates whether an MHTML fragment is created in place of a full MHTML document. An MHTML fragment includes the report content in a TABLE element and omits the HTML and BODY elements. The default value is **false**.|  
|**DataVisualizationFitSizing**|Indicates data visualization fit behavior when inside a tablix. This includes chart, gauge, and map.<br /><br /> The possible values are **Approximate** and **Exact**.<br /><br /> The default value is **Approximate**. If the setting is removed from the **rsreportserver.config** file then the default behavior is **Exact**.<br /><br /> Enabling **Exact** may have performance impact because the processing to determine the exact size may take longer.|  
  
## See Also  
 [Render](assetId:///M:ReportExecution2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,ReportExecution2005.Warning[]@,System.String[]@))   
 [Passing Device Information Settings to Rendering Extensions](../Topic/Passing%20Device%20Information%20Settings%20to%20Rendering%20Extensions.md)   
 [Customize Rendering Extension Parameters in RSReportServer.Config](../../Topics\TopicNameNotContainA/Customize-Rendering-Extension-Parameters-in-RSReportServer.Config.md)   
 [Technical Reference &#40;SSRS&#41;](../Topic/Technical%20Reference%20\(SSRS\).md)  
  
  