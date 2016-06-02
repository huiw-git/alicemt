---
title: Map Viewport Properties Dialog Box, Optimization
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c0310ba-eedd-4c9f-95bd-1f9e2a1a8ed3
robots: noindex,nofollow
---
# Map Viewport Properties Dialog Box, Optimization
  Select **Optimization** for the **Map Viewport Properties** dialog box to help control the resolution for viewing a map in a report.  
  
 When spatial data is embedded in the report, higher resolution means more data is stored in the report. When spatial data is not embedded in the report, higher resolution means that the report processor spends more time creating the map details. Lower resolution means less time waiting for the report to render.  
  
 Click the **Expression** \(*fx*\) button to edit an expression that sets the value of the option.  
  
## Options  
 **Performance**  
 Slide the pointer closer to **Performance** to simplify the map and display less detail.  
  
 **Quality**  
 Slide the pointer closer to **Quality** to draw the map with greater detail.  
  
 **Map resolution**  
 Specify a map resolution. This value specifies the smallest detail that you want to see in the rendered map in points.  
  
## See Also  
 [Maps &#40;Report Builder and SSRS&#41;](../Topic/Maps%20\(Report%20Builder%20and%20SSRS\).md)   
 [Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;](../Topic/Troubleshoot%20Reports:%20Map%20Reports%20\(Report%20Builder%20and%20SSRS\).md)  
  
  