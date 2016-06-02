---
title: Stock Charts (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
---
# Stock Charts (Report Builder and SSRS)
  A stock chart is specifically designed for financial or scientific data that uses up to four values per data point. These values align with the high, low, open and close values that are used to plot financial stock data. This chart type displays opening and closing values by using markers, which are typically lines or triangles. In the following example, the opening values are shown by the markers on the left, and the closing values are shown by the markers on the right.  
  
 ![Stock chart](../../Images\Image\ImageNotContaina/rs_StockChart.gif "rs_StockChart")  
  
 An example of a stock chart is available as a sample [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Report Builder report. For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)][Report Builder and Report Designer sample reports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Variations  
  
-   **Candlestick**. The candlestick chart is a specialized form of the stock chart, wherein boxes are used to show the range between the open and close values. Like the stock chart, the candlestick chart can display up to four values per data point.  
  
## Data Considerations for Stock Charts  
  
-   When presenting many stock data points, such as annual stock price trend, it is difficult to distinguish each open, close, high and low value of each data point. In this scenario, consider using a line chart instead of a stock chart.  
  
-   When axis labels are generated, labeling usually begins at zero.  In general, stock prices do not fluctuate to the same degree as other data sets. For this reason, you may want to disable the axis labels from starting at zero, in order to get a better view of your data. To do this, set **IncludeZero** to **false** in the **Axis Properties** dialog box or the Properties window. For more information about how the chart generates axis labels, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Axis%20Labels%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides many calculated formulas for use with stock charts, including Price Indicator, Relative Strength Index, MACD and more.  
  
## See Also  
 [Range Charts &#40;Report Builder and SSRS&#41;](../Topic/Range%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../Topic/Axis%20Properties%20Dialog%20Box,%20Axis%20Options%20\(Report%20Builder%20and%20SSRS\).md)  
  
  