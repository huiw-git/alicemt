---
title: Word Device Information Settings
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
---
# Word Device Information Settings
  The following table lists the device information settings for rendering in [!INCLUDE[ofprword](../../Token\Other/ofprword_md.md)] format.  
  
|Setting|Value|  
|-------------|-----------|  
|**AutoFit**|**False**. AutoFit is set to **false** set on any Word table.<br /><br /> **True**. AutoFit is set to **true** on every Word table.<br /><br /> **Never**. AutoFit values are not set on any Word table and behavior reverts to the Word default.<br /><br /> **Default**. AutoFit is set on tables that are narrower than the physical drawing area \(physical page width excluding margins\) per logical page.|  
|**ExpandToggles**|Indicates whether all items that can be toggled should render in their fully\-expanded state. The default value is **false**.|  
|**FixedPageWidth**|Indicates whether the Page Width written to the DOC file will grow to accommodate the width of the largest page in the Report Body. The default value is **false**.|  
|**OmitHyperlinks**|Indicates whether to omit the Hyperlink action on all items where it is set. The default value is **false**|  
|**OmitDrillthroughs**|Indicates whether to omit the Drillthrough action on all items where it is set. The default value is **false**|  
  
## See Also  
 [Render](assetId:///M:ReportExecution2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,ReportExecution2005.Warning[]@,System.String[]@))   
 [Passing Device Information Settings to Rendering Extensions](../Topic/Passing%20Device%20Information%20Settings%20to%20Rendering%20Extensions.md)   
 [Customize Rendering Extension Parameters in RSReportServer.Config](../../Topics\TopicNameNotContainA/Customize-Rendering-Extension-Parameters-in-RSReportServer.Config.md)   
 [Technical Reference &#40;SSRS&#41;](../Topic/Technical%20Reference%20\(SSRS\).md)  
  
  