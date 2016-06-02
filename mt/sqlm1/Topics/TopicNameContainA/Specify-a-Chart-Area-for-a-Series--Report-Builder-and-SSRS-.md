---
title: Specify a Chart Area for a Series (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
---
# Specify a Chart Area for a Series (Report Builder and SSRS)
  In [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated reports, the *chart* is the top\-level container that includes the outer border, the chart title, and the legend. By default, the chart contains one *chart area*. The chart area is not visible on the chart surface, but you can think of the chart area as a container that encompasses only the axis labels, the axis title and the plotting area of one or more series. The following illustration shows the concept of multiple chart areas within a single chart.  
  
 ![Shows a diagram of a chart area](../../Images\Image\ImageContaina/ChartAreasDiagram.gif "ChartAreasDiagram")  
  
 By default, all series are added to the default chart area. When using area, column, line, and scatter charts, any combination of these series can be displayed on the same chart area. If you have several series in the same chart area, the readability of the chart is reduced. You may want to separate the chart types into multiple chart areas. Using multiple chart areas will increase readability for easier comparisons. For example, price\-volume stock charts often have different ranges of values, but comparisons can be made between the price and volume data over the same period of time.  
  
 The bar, polar, or shape series can only be combined with series of the same chart types in the same chart area. If you are using a Polar or Shape chart, consider using a separate chart data region for each field that you wish to show.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## To associate a series with a new chart area  
  
1.  Right\-click anywhere on the chart and select **Add New Chart Area**. A new, blank chart area appears on the chart.  
  
2.  Right\-click the series on the chart or right\-click a series or data field in the appropriate area in the Chart Data pane, and then click **Series Properties**.  
  
3.  In **Axes and Chart Areas**, select the chart area that you want the series to be shown in.  
  
4.  \(Optional\) Align the chart areas vertically. To do this, right\-click the chart and select **Chart Area Properties**. In **Alignment**, select another chart area that you want to align the selected chart area with.  
  
## See Also  
 [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Multiple%20Series%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Data%20Points%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](../Topic/Define%20Colors%20on%20a%20Chart%20Using%20a%20Palette%20\(Report%20Builder%20and%20SSRS\).md)   
 [Polar Charts &#40;Report Builder and SSRS&#41;](../Topic/Polar%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Shape Charts &#40;Report Builder and SSRS&#41;](../Topic/Shape%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Pie Charts &#40;Report Builder and SSRS&#41;](../Topic/Pie%20Charts%20\(Report%20Builder%20and%20SSRS\).md)  
  
  