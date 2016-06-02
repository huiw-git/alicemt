---
title: Polar Charts (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9402d8f-202a-4cdf-949e-50f5b1d2b885
---
# Polar Charts (Report Builder and SSRS)
  A polar chart displays a series as a set of points that are grouped by category on a 360\-degree circle. Values are represented by the length of the point as measured from the center of the circle. The farther the point is from the center, the greater its value. Category labels are displayed on the perimeter of the chart. For more information on how to add data to a polar chart, see [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Variations  
  
-   **Radar chart**. A radar chart displays a series as a circular line or area. Unlike the polar chart, the radar chart does not display data in terms of polar coordinates.  
  
## Data Considerations for Polar Charts  
  
-   The radar chart is useful for comparisons between multiple series of category data.  
  
-   Polar charts are most commonly used to graph polar data, where each data point is determined by an angle and a distance.  
  
-   Polar charts cannot be combined with any other chart type in the same chart area.  
  
## Example  
 The following example shows how a radar chart can be used. The table below provides sample data for the chart.  
  
|Name|Sales|  
|----------|-----------|  
|Shrubs|61|  
|Seeds|78|  
|Bulbs|60|  
|Trees|38|  
|Flowers|81|  
  
 In this example, the Name field is placed in the Category Groups area. The Sales field is placed in the Values area. The Sales field is automatically aggregated for the chart when you drop it. The radar chart calculates where to place the labels based on the number of values in the Sales field, which contains five values and places labels at five equidistant points on a circle. If the Sales field contained three values, the labels would be placed at three equidistant points on a circle.  
  
 The following illustration shows an example of a radar chart based on the data presented.  
  
 ![Radar chart](../../Images\Image\ImageNotContaina/rs_RadarChart.gif "rs_RadarChart")  
  
## See Also  
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Chart Types &#40;Report Builder and SSRS&#41;](../Topic/Chart%20Types%20\(Report%20Builder%20and%20SSRS\).md)   
 [Line Charts &#40;Report Builder and SSRS&#41;](../Topic/Line%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](../Topic/Empty%20and%20Null%20Data%20Points%20in%20Charts%20\(Report%20Builder%20and%20SSRS\).md)  
  
  