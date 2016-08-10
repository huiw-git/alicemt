---
title: "Range Charts (Report Builder and SSRS)"
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
ms.assetid: 48e351d3-ac5b-4eda-a4bd-32a0de206a30
caps.latest.revision: 6
caps.handback.revision: 0
manager: mblythe
---
# Range Charts (Report Builder and SSRS)
A range chart type displays a set of data points that are each defined by multiple values for the same category. Values are represented by the height of the marker as measured by the value axis. Category labels are displayed on the category axis. The plain range chart fills in the area between the top and bottom value for each data point.  
  
 The following illustration shows a plain range chart with three series.  
  
 ![Range chart](../../Topics/TopicNameNotContainA/images/rs_RangeChart.gif "rs_RangeChart")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
## Variations  
  
-   **Smooth range**. A smooth range chart displays curved lines rather than straight.  
  
-   **Column range**. A column range chart uses columns instead of areas to display the ranges.  
  
-   **Bar range**. A bar range chart uses bars instead of areas to display the ranges.  
  
## Data Considerations for Range Charts  
  
-   Range chart types require two values per data point. These values correspond with a high value and a low value that defines the range for each data point.  
  
-   Range charts are useful for analysis only if the top values are always higher than the bottom values. If this is not the case, consider using a line chart. If the high value is lower the low value, the range chart will display the absolute value of the difference between these values.  
  
-   If only one value is specified, the range chart will display as if it were a regular area chart, with one value per data point.  
  
-   Range charts are often used to graph data that contains minimum and maximum values for each category group in the dataset.  
  
-   Displaying markers on each data point is not supported on the range chart.  
  
-   Like the area chart, in a plain range chart, if the values in multiple series are similar, the series will overlap. In this scenario, you may want to use a column range or bar range chart instead of a plain range chart.  
  
-   Gantt charts can be created using a range bar chart.  
  
## See Also  
 [Charts (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Charts--Report-Builder-and-SSRS-.md)   
 [Chart Types (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Chart-Types--Report-Builder-and-SSRS-.md)   
 [Formatting a Chart (Report Builder and SSRS)](../../Topics/TopicNameContainA/Formatting-a-Chart--Report-Builder-and-SSRS-.md)