---
title: ATOM Device Information Settings
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
---
# ATOM Device Information Settings
  The device information settings for the Atom rendering extension support submittal of the name of an Atom feed and character encoding to use.  
  
 The following table lists the device information settings for rendering to a data service document.  
  
|Setting|Value|  
|-------------|-----------|  
|**DataFeed**|If specified, renders the Atom feed corresponding to the feed name provided in this setting. If not, renders the Atom service document for the report. The unique auto\-generated identifier of the data feed. This  value is used internally and you should not change it.|  
|**Encoding**|The Internet Assigned Numbers Authority \(IANA\) name of a character encoding that is supported by the .NET Framework. The default value is **UTF\-8**. Examples of other values include ASCII, UTF\-7, and UTF\-16.|  
  
## See Also  
 [Render](assetId:///M:ReportExecution2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,ReportExecution2005.Warning[]@,System.String[]@))   
 [Passing Device Information Settings to Rendering Extensions](../Topic/Passing%20Device%20Information%20Settings%20to%20Rendering%20Extensions.md)   
 [Customize Rendering Extension Parameters in RSReportServer.Config](../../Topics\TopicNameNotContainA/Customize-Rendering-Extension-Parameters-in-RSReportServer.Config.md)   
 [Technical Reference &#40;SSRS&#41;](../Topic/Technical%20Reference%20\(SSRS\).md)  
  
  