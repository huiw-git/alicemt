---
title: Hide Legend Items on the Chart (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
---
# Hide Legend Items on the Chart (Report Builder and SSRS)
  By default, any series added to a non\-Shape chart will be added as an item in the legend. For pie, doughnut, funnel, and pyramid charts, any series added to the chart will add individual data points in the legend.  
  
 You can hide any item on the legend. When you hide a legend item, it will still appear in the chart. This is useful in situations where you do not want to show more information for a series that is added to the chart. For example, if you have added a calculated series like a moving average to the chart, you may want to hide this entry in the legend so that more information is only shown for the original series.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To hide an item from display in the legend  
  
1.  Right\-click on the series you want to hide and select **Series Properties**.  
  
2.  Click **Legend**. Select the **Do not show this series in a legend** option.  
  
    > [!NOTE]  
    >  You cannot hide a series for one group and not for the others. If you have added a field to the **Series Groups** area, all series belonging to this group will be hidden.  
  
## See Also  
 [Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20the%20Legend%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Data%20Points%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](../Topic/Change%20the%20Text%20of%20a%20Legend%20Item%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Moving%20Average%20to%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Legend Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../Topic/Legend%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder%20and%20SSRS\).md)  
  
  