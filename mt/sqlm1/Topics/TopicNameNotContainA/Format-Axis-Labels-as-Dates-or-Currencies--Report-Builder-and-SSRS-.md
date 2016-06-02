---
title: Format Axis Labels as Dates or Currencies (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
---
# Format Axis Labels as Dates or Currencies (Report Builder and SSRS)
  When you show properly formatted DateTime values on an axis, a chart will automatically display these values as days. To specify a date\/time interval for the x\-axis, such as an interval of months or an interval of hours, you must format the axis labels and set the type of axis interval to a valid date or time interval.  
  
> [!NOTE]  
>  In column and scatter charts, the horizontal, or x\-axis, is the category axis. In bar charts, the vertical, or y\-axis, is the category axis.  
  
 In order to format time intervals correctly, the values displayed on the x\-axis must evaluate to a [System.DateTime](assetId:///T:System.DateTime) data type. If your field has a data type of [System.String](assetId:///T:System.String), the chart will not calculate intervals as dates or times. For more information, see [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md).  
  
 When a numeric value is added to the y\-axis, by default, the chart does not format the number before displaying it. If your numeric field is a sales figure, consider formatting the numbers as currencies to increase the readability of the chart.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To format x\-axis labels as monthly intervals  
  
1.  Right\-click the horizontal, or x\-axis, of the chart, and select **HorizontalAxis Properties**.  
  
2.  In the **HorizontalAxis Properties** dialog box, select **Number**.  
  
3.  From the **Category** list, select **Date**. From the **Type** list, select a date format to apply to the x\-axis labels.  
  
4.  Select **Axis Options.**  
  
5.  In **Interval**, type **1**. In **Interval type** property, select **Months**.  
  
    > [!NOTE]  
    >  If you do not specify an interval type, the chart will calculate intervals in terms of days.  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
### To format y\-axis labels using a currency format  
  
1.  Right\-click the vertical, or y\-axis, of the chart, and select **VerticalAxis Properties**.  
  
2.  In the **VerticalAxis Properties** dialog box, select **Number**.  
  
3.  From the **Category** list, select **Currency**. From the **Symbol** list, select a currency format to apply to the y\-axis labels.  
  
4.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Axis%20Labels%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](../Topic/Specify%20a%20Logarithmic%20Scale%20\(Report%20Builder%20and%20SSRS\).md)   
 [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](../Topic/Specify%20an%20Axis%20Interval%20\(Report%20Builder%20and%20SSRS\).md)  
  
  