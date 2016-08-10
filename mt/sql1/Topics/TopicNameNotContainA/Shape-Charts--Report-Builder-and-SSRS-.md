---
title: "Shape Charts (Report Builder and SSRS)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b8404c1-aa89-4350-8bd6-203bc0446ee4
caps.latest.revision: 9
caps.handback.revision: 0
manager: mblythe
---
# Shape Charts (Report Builder and SSRS)
A shape chart displays value data as percentages of a whole. Shape charts are typically used to show proportional comparisons between different values in a set. Categories are represented by individual segments of the shape. The size of the segment is determined by the value. Shape charts are similar in use to pie charts, except that they order categories from largest to smallest.  
  
 A funnel chart displays values as progressively decreasing proportions. The size of the area is determined by the series value as a percentage of the total of all values. For example, you might use a funnel chart to display Web site visitor trends. It is likely that the funnel chart will display a wide area at the top, indicating visitor page hits to the homepage, and the other areas will be proportionally smaller. For more information about how to add data to a funnel chart, see [Charts (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Charts--Report-Builder-and-SSRS-.md).  
  
 The following illustration shows an example of a funnel chart.  
  
 ![Funnel chart](../../Topics/TopicNameNotContainA/images/rs_FunnelChart.gif "rs_FunnelChart")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
## Variations  
  
-   **Pyramid**. A pyramid chart displays proportional data so that the chart looks like a pyramid.  
  
## Data Considerations for Shape Charts  
  
-   Shape charts are popular in reports because of their visual impact. However, shape charts are a very simplified chart type that may not best represent your data. Consider using a shape chart only once the data has been aggregated to seven data points or less. In general, use the shape chart to display only one category per data region.  
  
-   Shape charts display each data group as a separate segment of the chart. You must add at least one data field and one category field. If more than one data field is added to a shape chart, the shape chart will display both data fields in the same chart.  
  
-   Shape charts are most effective for showing proportional percentages in sorted order. However, in order to maintain consistency, the chart does not sort the values in your dataset by default. Consider ordering your values from highest to lowest to most accurately represent your data as a funnel or a pyramid. For more information, see [Filter, Group, and Sort Data (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Filter--Group--and-Sort-Data--Report-Builder-and-SSRS-.md).  
  
-   Null, empty, negative and zero values have no effect when calculating ratios. For this reason, these values are not shown on a shape chart. If you want to visually indicate these types of values on your chart, change the chart type to be something other than a shape chart. For more information about how to add empty points to a non-shape chart, see [Add Empty Points to a Chart (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-Empty-Points-to-a-Chart--Report-Builder-and-SSRS-.md).  
  
-   If you are defining your own colors on a shape chart using a custom palette, be sure that you have enough colors in your palette to highlight each data point with its own unique color. For more information, see [Formatting Series Colors on a Chart (Report Builder and SSRS)](../../Topics/TopicNameContainA/Formatting-Series-Colors-on-a-Chart--Report-Builder-and-SSRS-.md).  
  
-   Unlike all other chart types, a shape chart will display individual data points, and not individual series, in its legend.  
  
-   Settings for the value and category axis are ignored for funnel charts. If you have multiple category or series groups, the group labels are displayed in the chart legend.  
  
-   Shape chart types cannot be combined with any other chart type in the same chart area. If you have to show comparisons between data displayed on a shape chart, and data displayed on another chart type, you will need to add a second chart area.  
  
-   Adding 3-D effects significantly improves the overall appearance of a shape chart type.  
  
-   You can apply additional drawing styles to pie and doughnut charts for increased visual impact. See [Formatting Series Colors on a Chart (Report Builder and SSRS)](../../Topics/TopicNameContainA/Formatting-Series-Colors-on-a-Chart--Report-Builder-and-SSRS-.md) for more information.  
  
## See Also  
 [Charts (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Charts--Report-Builder-and-SSRS-.md)   
 [Formatting a Chart (Report Builder and SSRS)](../../Topics/TopicNameContainA/Formatting-a-Chart--Report-Builder-and-SSRS-.md)   
 [Empty and Null Data Points in Charts (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Empty-and-Null-Data-Points-in-Charts--Report-Builder-and-SSRS-.md)   
 [Pie Charts (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Pie-Charts--Report-Builder-and-SSRS-.md)