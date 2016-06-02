---
title: Position Labels in a Chart (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
---
# Position Labels in a Chart (Report Builder and SSRS)
  Because each chart type has a different shape, data point labels are placed in an optimal location so as not to interfere on the chart. The default position of the labels depends varies with the chart type:  
  
-   On stacked charts, labels can only be positioned inside the series.  
  
-   On funnel or pyramid charts, labels are placed on the outside in a column.  
  
-   On pie charts, labels are placed inside the individual slices on a pie chart.  
  
-   On bar charts, labels are placed outside of the bars that represent data points.  
  
-   On polar charts, labels are placed outside of the circular area that represents data points.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## To change the position of point labels in a Pie chart  
  
1.  Create a pie chart.  
  
2.  On the design surface, right\-click the chart and select **Show Data Labels**.  
  
3.  Open the Properties pane. On the **View** tab, click **Properties**.  
  
4.  On the design surface, click the chart. The properties for the chart are displayed in the Properties pane.  
  
5.  In the **General** section, expand the **CustomAttributes** node. A list of attributes for the pie chart is displayed.  
  
6.  Select a value for the PieLabelStyle property.  
  
## To change the position of point labels in a Funnel or Pyramid chart  
  
1.  Create a funnel or pyramid chart.  
  
2.  On the design surface, right\-click the chart and select **Show Data Labels**.  
  
3.  Open the Properties pane. On the **View** tab, click **Properties**  
  
4.  On the design surface, click the chart. The properties for the chart are displayed in the Properties pane.  
  
5.  In the **General** section, expand the **CustomAttributes** node. A list of attributes for the funnel chart is displayed.  
  
6.  For a funnel chart, select a value for the FunnelLabelStyle property. For a pyramid chart, select a value for the PyramidLabelStyle property.  
  
    > [!NOTE]  
    >  When this property is set to a value **OutsideInColumn**, the labels are drawn in a vertical column. There is no way to change the position of the column.  
  
## To change the position of point labels in a Bar chart  
  
1.  Create a bar chart.  
  
2.  On the design surface, right\-click the chart and select **Show Data Labels**.  
  
3.  Open the Properties pane. On the **View** tab, click **Properties**  
  
4.  On the design surface, click the chart. The properties for the chart are displayed in the Properties pane.  
  
5.  In the **General** section, expand the **CustomAttributes** node. A list of attributes for the bar chart is displayed.  
  
6.  Select a value for the BarLabelStyle property.  
  
 When the bar label style is set to **Outside**, the labels will be placed outside of the bar, as long as it fits in the chart area. If the label cannot be placed outside of the bar but inside of the chart area, the label is placed inside the bar at the position closest to the end of the bar.  
  
## To change the position of point labels in an Area, Column, Line or Scatter chart  
  
1.  Create an Area, Column, Line or Scatter chart.  
  
2.  On the design surface, right\-click the chart and select **Show Data Labels**.  
  
3.  Open the Properties pane. On the **View** tab, click **Properties**  
  
4.  On the design surface, click the series. The properties for the series are displayed in the Properties pane.  
  
5.  In the **Data** section, expand the **DataPoint** node, then expand the **Label**node.  
  
6.  Select a value for the Position property.  
  
## See Also  
 [Pie Charts &#40;Report Builder and SSRS&#41;](../Topic/Pie%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Bar Charts &#40;Report Builder and SSRS&#41;](../Topic/Bar%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Axis%20Labels%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](../Topic/Format%20Axis%20Labels%20as%20Dates%20or%20Currencies%20\(Report%20Builder%20and%20SSRS\).md)   
 [Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](../Topic/Display%20Data%20Point%20Labels%20Outside%20a%20Pie%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Data%20Points%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)  
  
  