---
title: Area Charts (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 245b236d-1d55-4744-b752-80bd133502aa
---
# Area Charts (Report Builder and SSRS)
  An area chart displays a series as a set of points connected by a line, with all the area filled in below the line. For more information on how to add data to an area chart, see [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md).  
  
 The following illustration shows an example of a stacked area chart. The data is well suited for display on a stacked area chart because the chart can display totals for all series as well as the proportion that each series contributes to the total.  
  
 ![Area chart](../../Images\Image\ImageNotContaina/AreaChart.gif "AreaChart")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Variations  
  
-   **Stacked area**. An area chart where multiple series are stacked vertically. If there is only one series in your chart, the stacked area chart will display the same as an area chart.  
  
-   **Percent stacked area**. An area chart where multiple series are stacked vertically to fit the entire chart area. If there is only one series in your chart, the stacked area chart will display the same as an area chart.  
  
-   **Smooth area**. An area chart where the data points are connected by a smooth line instead of a regular line. Use a smooth area chart instead of an area chart when you are more concerned with displaying trends than with displaying the values of individual data points.  
  
## Data Considerations for Area Charts  
  
-   Along with the line chart, the area chart is the only chart type that displays data contiguously. For this reason, an area chart is commonly used to represent data that occurs over a continuous period of time.  
  
-   A percent stacked area chart is useful for showing proportional data that occurs over time.  
  
-   If there is only one series, a stacked area chart will be drawn as an area chart.  
  
-   In a plain area chart, if the values in multiple series are similar, the areas may overlap, obscuring important data point values. You can resolve this issue by changing the chart type to a stacked area chart, which is designed to show multiple series on an area chart.  
  
-   If your stacked area chart contains gaps, it is possible that your dataset includes empty values, which will be shown as a vacant section on a stacked area chart. If your dataset includes empty values, consider inserting empty points on the chart. Adding empty points will fill in the empty areas on the chart with a different color to indicate null or zero values. For more information, see [Add Empty Points to a Chart &#40;Report Builder and SSRS&#41;](../Topic/Add%20Empty%20Points%20to%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   Area chart types are very similar to column and line charts in behavior. If you are making a comparison between multiple series, consider using a column chart instead. If you are analyzing trends over a period of time, consider using a line chart.  
  
## See Also  
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Chart Types &#40;Report Builder and SSRS&#41;](../Topic/Chart%20Types%20\(Report%20Builder%20and%20SSRS\).md)   
 [Line Charts &#40;Report Builder and SSRS&#41;](../Topic/Line%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Change a Chart Type &#40;Report Builder and SSRS&#41;](../Topic/Change%20a%20Chart%20Type%20\(Report%20Builder%20and%20SSRS\).md)   
 [Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](../Topic/Empty%20and%20Null%20Data%20Points%20in%20Charts%20\(Report%20Builder%20and%20SSRS\).md)  
  
  