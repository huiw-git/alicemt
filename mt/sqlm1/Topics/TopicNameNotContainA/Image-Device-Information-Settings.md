---
title: Image Device Information Settings
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
---
# Image Device Information Settings
  The following table lists the device information settings for rendering in IMAGE format.  
  
|Setting|Value|  
|-------------|-----------|  
|**Columns**|The number of columns to set for the report. This value overrides the report's original settings.|  
|**ColumnSpacing**|The column spacing to set for the report. This value overrides the report's original settings.|  
|**DpiX**|The horizontal resolution of the output image. The default value is **96**. Applies to **BMP**, **GIF**, **PNG**, and **TIFF** output formats.|  
|**DpiY**|The vertical resolution of the output image. The default value is **96**. Applies to **BMP**, **GIF**, **PNG**, and **TIFF** output formats.|  
|**EndPage**|The last page of the report to render. The default value is the value for **StartPage**.|  
|**MarginBottom**|The bottom margin value, in inches, to set for the report. You must include an integer or decimal value followed by "in" \(for example, **1in**\). This value overrides the report's original settings.|  
|**MarginLeft**|The left margin value, in inches, to set for the report. You must include an integer or decimal value followed by "in" \(for example, **1in**\). This value overrides the report's original settings.|  
|**MarginRight**|The right margin value, in inches, to set for the report. You must include an integer or decimal value followed by "in" \(for example, **1in**\). This value overrides the report's original settings.|  
|**MarginTop**|The top margin value, in inches, to set for the report. You must include an integer or decimal value followed by "in" \(for example, **1in**\). This value overrides the report's original settings.|  
|**OutputFormat**|One of the [!INCLUDE[ndptecgdiexpanded](../../Token\Other/ndptecgdiexpanded_md.md)] \([!INCLUDE[ndptecgdi](../../Token\Other/ndptecgdi_md.md)]\) supported output formats: **BMP**, **EMF**, **GIF**, **JPEG**, **PNG**, or **TIFF**.|  
|**PageHeight**|The page height, in inches, to set for the report. You must include an integer or decimal value followed by "in" \(for example, **11in**\). This value overrides the report's original settings.|  
|**PageWidth**|The page width, in inches, to set for the report. You must include an integer or decimal value followed by "in" \(for example, **8.5in**\). This value overrides the report's original settings.|  
|**PrintDpiX**|The horizontal resolution of the output image. The default value is **300**. Applies to the Enhanced MetaFile \(**EMF**\) output format.|  
|**PrintDpiY**|The vertical resolution of the output image. The default value is **300**. Applies to the Enhanced MetaFile \(**EMF**\) output format.|  
|**StartPage**|The first page of the report to render. A value of **0** indicates that all pages are rendered. The default value is **1**.|  
  
## See Also  
 [Render](assetId:///M:ReportExecution2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,ReportExecution2005.Warning[]@,System.String[]@))   
 [Passing Device Information Settings to Rendering Extensions](../Topic/Passing%20Device%20Information%20Settings%20to%20Rendering%20Extensions.md)   
 [Customize Rendering Extension Parameters in RSReportServer.Config](../../Topics\TopicNameNotContainA/Customize-Rendering-Extension-Parameters-in-RSReportServer.Config.md)   
 [Technical Reference &#40;SSRS&#41;](../Topic/Technical%20Reference%20\(SSRS\).md)  
  
  