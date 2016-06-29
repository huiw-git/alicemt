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
By default, any series added to a non-Shape chart in a [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] paginated report will be added as an item in the legend. For pie, doughnut, funnel, and pyramid charts, any series added to the chart will add individual data points in the legend.  
  
 You can hide any item on the legend. When you hide a legend item, it will still appear in the chart. This is useful in situations where you do not want to show more information for a series that is added to the chart. For example, if you have added a calculated series like a moving average to the chart, you may want to hide this entry in the legend so that more information is only shown for the original series.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/includes/ssRBRDDup_md.md)]  
  
## To hide an item from display in the legend  
  
1.  Right-click on the series you want to hide and select **Series Properties**.  
  
2.  Click **Legend**. Select the **Do not show this series in a legend** option.  
  
    > [!NOTE]  
    >  You cannot hide a series for one group and not for the others. If you have added a field to the **Series Groups** area, all series belonging to this group will be hidden.  
  
## See Also  
 [Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Formatting-the-Legend-on-a-Chart--Report-Builder-and-SSRS-.md)   
 [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Formatting-Data-Points-on-a-Chart--Report-Builder-and-SSRS-.md)   
 [Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Change-the-Text-of-a-Legend-Item--Report-Builder-and-SSRS-.md)   
 [Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-a-Moving-Average-to-a-Chart--Report-Builder-and-SSRS-.md)   
 [Legend Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Legend-Properties-Dialog-Box--General--Report-Builder-and-SSRS-.md)  
  
  