---
title: Add a Moving Average to a Chart (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
---
# Add a Moving Average to a Chart (Report Builder and SSRS)
  A moving average is an average of the data in your series, calculated over a defined period of time. The moving average can be shown on the chart to identify significant trends.  
  
 The Moving Average formula is the most popular price indicator used in technical analyses. Many other formulas, including mean, median and standard deviation, can also be derived from a series on the chart. When specifying a moving average, each formula may have one or more parameters that must be specified.  
  
 When a moving average formula is added in Design mode, the line series that is added is only a visual placeholder. The chart will calculate the data points of each formula during report processing.  
  
 Built\-in support for trend lines is not available in [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To add a calculated moving average to a series on the chart  
  
1.  Right\-click on a field in the **Values** area and click **Add Calculated Series**. The **Calculated Series Properties** dialog box opens.  
  
2.  Select the **Moving average** option from the **Formula** drop\-down list.  
  
3.  Specify an integer value for the **Period** that represents the period of the moving average.  
  
    > [!NOTE]  
    >  The period is the number of days used to calculate a moving average. If date\/time values are not specified on the x\-axis, the period is represented by the number of data points used to calculate a moving average. If there is only one data point, the moving average formula does not calculate. The moving average is calculated starting at the second point. If you specify the **Start from first point** option, the chart will start the moving average at the first point. If there is only one data point, the point in the calculated moving average will be identical to the first point in your original series.  
  
## See Also  
 [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add Empty Points to a Chart &#40;Report Builder and SSRS&#41;](../Topic/Add%20Empty%20Points%20to%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)  
  
  