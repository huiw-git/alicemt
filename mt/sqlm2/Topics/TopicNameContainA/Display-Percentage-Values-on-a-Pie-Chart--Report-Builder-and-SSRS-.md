---
title: Display Percentage Values on a Pie Chart (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
---
# Display Percentage Values on a Pie Chart (Report Builder and SSRS)
  By default, categories are shown in the legend to identify each value. If you have labeled the pie chart using category labels, you may want show percentages in the legend.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To display percentage values as labels on a pie chart  
  
1.  Add a pie chart to your report. For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](../../Topics\TopicNameContainA/Add-a-Chart-to-a-Report--Report-Builder-and-SSRS-.md).  
  
2.  On the design surface, right\-click on the pie and select **Show Data Labels**. The data labels should appear within each slice on the pie chart.  
  
3.  On the design surface, right\-click on the labels and select **Series Label Properties**. The **Series Label Properties** dialog box appears.  
  
4.  Type **\#PERCENT** for the **Label data** option.  
  
5.  \(Optional\) To specify how many decimal places the label shows, type "\#PERCENT{P*n*}" where *n* is the number of decimal places to display. For example, to display no decimal places, type "\#PERCENT{P0}".  
  
### To display percentage values in the legend of a pie chart  
  
1.  On the design surface, right\-click on the pie chart and select **Series Properties**. The **Series Properties** dialog box displays.  
  
2.  In **Legend**, type **\#PERCENT** for the **Custom legend text** property.  
  
## See Also  
 [Pie Charts &#40;Report Builder and SSRS&#41;](../../Topics\TopicNameNotContainA/Pie-Charts--Report-Builder-and-SSRS-.md)   
 [Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](../../Topics\TopicNameContainA/Formatting-the-Legend-on-a-Chart--Report-Builder-and-SSRS-.md)   
 [Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](../../Topics\TopicNameContainA/Display-Data-Point-Labels-Outside-a-Pie-Chart--Report-Builder-and-SSRS-.md)   
 [Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;](../../Topics\TopicNameContainA/Collect-Small-Slices-on-a-Pie-Chart--Report-Builder-and-SSRS-.md)  
  
  