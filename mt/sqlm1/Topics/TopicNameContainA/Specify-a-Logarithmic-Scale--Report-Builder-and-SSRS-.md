---
title: Specify a Logarithmic Scale (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
---
# Specify a Logarithmic Scale (Report Builder and SSRS)
  If you have data that is logarithmically proportional, you may want to consider using a logarithmic scale on a chart in a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report. This helps improve the appearance of the chart by making your data more manageable. Most logarithmic scales use a base of 10.  
  
 This feature is only available on the value axis. The value axis is usually the vertical, or y\-axis. On bar charts, however, it is the horizontal, or x\-axis.  
  
 If your axis is logarithmic, all other properties relating to the axis will be scaled logarithmically. For example, if you specify a base\-10 logarithmic scale on your axis, setting an axis interval of 2 will generate intervals in magnitudes of 10 to the power of 2, or 100. This means your axis values will read 1, 100, 10000, instead of the default result of 1, 10, 100, 1000, 10000.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## To specify a logarithmic scale  
  
1.  Right\-click the y\-axis of your chart, and click **VerticalAxis Properties**. The **VerticalAxis Properties** dialog box appears.  
  
2.  In **Axis Options**, select **Uselogarithmic scale**.  
  
3.  In the **Logbase** text box, type a positive value for the logarithmic base. If no value is specified, the logarithmic base defaults to 10.  
  
## See Also  
 [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Axis%20Labels%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](../Topic/Format%20Axis%20Labels%20as%20Dates%20or%20Currencies%20\(Report%20Builder%20and%20SSRS\).md)   
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)  
  
  