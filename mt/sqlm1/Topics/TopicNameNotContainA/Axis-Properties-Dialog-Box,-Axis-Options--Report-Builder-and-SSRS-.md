---
title: Axis Properties Dialog Box, Axis Options (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
---
# Axis Properties Dialog Box, Axis Options (Report Builder and SSRS)
  Select **Axis Options** on the **Horizontal** or **VerticalAxis Properties** dialog box to define the appearance of the specified axis of the chart. In previous versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], the chart displayed all labels on the x\-axis by default. However, in [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] 2008, the chart skips labels in order to produce a cleaner image on the chart and avoid labeling collisions. For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Axis%20Labels%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Options  
 **Enable scale breaks**  
 Select this option to enable the chart to draw a scale breaks when it is deemed necessary. When this option is enabled, the chart will automatically calculate whether there is sufficient difference between the high and low points in the dataset to draw a scale break.  
  
 **Reverse direction**  
 Select this option to reverse the direction of the chart. For example, by default, a column chart displays the y\-axis on the left side of the chart and categories from left to right. When this option is selected, the chart displays the y\-axis on the right side of the chart and categories from right to left.  
  
 **Use interlacing color**  
 Select this option to add strip lines to the chart, and then select a color or type an expression. Strip lines are shaded bands on the chart area that give the effect of alternating light and dark areas between gridlines. These strip lines are useful for highlighting repeating patterns on an axis.  
  
 **Always include zero**  
 Select this option to always include zero on the axis scale. If this option is not enabled, the chart will not label the zero value on the axis. Including zero values is useful when the dataset includes negative or zero values.  
  
 **Scalar axis**  
 Select this option to display a set of axis values on a continuous scale. For example, if the dataset contains data for January, March, and November, a non\-scalar axis displays only those months, whereas a scalar axis displays all of the months in the year.  
  
 **Use logarithmic scale**  
 Select this option to indicate that the axis scale is logarithmic. This option is available only on the y\-axis if the axis contains positive numeric values.  
  
 In the box, type the logarithmic base to use when the axis is set to use a logarithmic scale. By default, the chart uses a base of 10 for the logarithmic scale of an axis. This option is available only on the y\-axis if the axis is numeric.  
  
 **Minimum**  
 Type an expression or a value for the minimum value for the x\-axis. If omitted, the minimum value is determined by the data returned by the dataset.  
  
 **Maximum**  
 Type an expression or a value for the maximum value for the x\-axis. If omitted, the maximum value is determined by the data returned by the dataset.  
  
 **Interval**  
 Type an expression or value for the interval between axis labels. For example, type 1 to display each category label on the axis. Type 2 to display every other category label. If omitted, the labels are calculated automatically based on the values in the dataset.  
  
 **Interval type**  
 Type an expression or a value for the interval type of the interval specified. For example, if you want the interval to be two days, you will specify **2** for interval and **Days** for interval type.  
  
 **Side margins**  
 Type an expression or select a value to add or remove a margin between the chart elements and the sides of the chart. If this option is set to **Auto**, a side margins are added.  
  
## See Also  
 [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Axis%20Labels%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Series%20Colors%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](../Topic/Specify%20an%20Axis%20Interval%20\(Report%20Builder%20and%20SSRS\).md)   
 [Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](../Topic/Format%20Axis%20Labels%20as%20Dates%20or%20Currencies%20\(Report%20Builder%20and%20SSRS\).md)   
 [Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;](../Topic/Plot%20Data%20on%20a%20Secondary%20Axis%20\(Report%20Builder%20and%20SSRS\).md)   
 [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](../Topic/Sparklines%20and%20Data%20Bars%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;](../Topic/Add%20or%20Remove%20Margins%20from%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)  
  
  