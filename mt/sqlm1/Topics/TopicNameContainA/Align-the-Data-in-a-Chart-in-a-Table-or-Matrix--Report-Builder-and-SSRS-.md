---
title: Align the Data in a Chart in a Table or Matrix (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
---
# Align the Data in a Chart in a Table or Matrix (Report Builder and SSRS)
  Sparklines and data bars are small, simple charts that convey a lot of information with little extraneous detail. In a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report, when you check this option the values in your sparklines and data bars will align across the different cells in the table or matrix, even if there are missing values in the data they are based on.  
  
 ![rs_SparklineAlignData](../../Images\Image\ImageNotContaina/rs_SparklineAlignData.gif "rs_SparklineAlignData")  
  
 In this image, the column chart shows daily sales for each employee. Note that for days that an employee has no sales, the chart leaves a blank and aligns subsequent days horizontally. It also aligns the charts vertically by making the sizes of the different charts relative to each other. For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](../Topic/Sparklines%20and%20Data%20Bars%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Align the data in a sparkline or data bar  
  
1.  [Add a sparkline or data bar](Add%20Sparklines%20and%20Data%20Bars%20\(Report%20Builder%20and%20SSRS\).md) to a table or matrix.  
  
2. Click in the sparkline or data bar, and then click **Horizontal Axis Properties** or **Vertical Axis Properties**.  
  
2.  On the **Axis Options** tab, check the **Align axes in** box, and then in the dropdown box, select the group on which to align the axis.  
  
3.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](../Topic/Add%20Sparklines%20and%20Data%20Bars%20\(Report%20Builder%20and%20SSRS\).md)  
  
  