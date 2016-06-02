---
title: Add Sparklines and Data Bars (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
---
# Add Sparklines and Data Bars (Report Builder and SSRS)
  Sparklines and data bars are small, spare charts that convey a lot of information with little extraneous detail. For more information about them, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](../Topic/Sparklines%20and%20Data%20Bars%20\(Report%20Builder%20and%20SSRS\).md).  
  
 In [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated reports, sparklines and data bars are most commonly placed in cells in a table or matrix. Sparklines usually display only one series each. Data bars can contain one or more data points. Both sparklines and data bars derive their impact from repeating the series information for each row in the table or matrix.  
  
## To add a sparkline or data bar to a table or matrix  
  
1.  If you have not done so already, create a [table](../Topic/Tables%20\(Report%20Builder%20%20and%20SSRS\).md) or [matrix](Create%20a%20Matrix%20\(Report%20Builder%20and%20SSRS\).md) with the data you want to display.  
  
2.  Insert a column in your table or matrix. For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](../Topic/Insert%20or%20Delete%20a%20Column%20\(Report%20Builder%20and%20SSRS\).md).  
  
3.  On the **Insert** tab, click **Sparkline** or **Data Bar**, and then click in a cell in the new column.  
  
    > [!NOTE]  
    >  You cannot place sparklines in a detail group in a table. They must go in a cell associated with a group.  
  
4.  In the **Change Sparkline\/Data Bar Type** dialog box, click the kind of sparkline or data bar you want, and then click **OK**.  
  
5.  Click the sparkline or data bar.  
  
     The **Chart Data** pane opens.  
  
6.  In the **Values** area, click the **Add Fields** plus sign \(**\+**\), and then click the field whose values you want charted.  
  
7.  In the **Category Groups** area, click the **Add Fields** plus sign \(**\+**\), and then click the field whose values you want to group by.  
  
     Typically for sparklines and data bars, you will not add a field to the **Series Group** area because you only want one series for each row.  
  
## See Also  
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Align the Data in a Chart in a Table or Matrix &#40;Report Builder and SSRS&#41;](../Topic/Align%20the%20Data%20in%20a%20Chart%20in%20a%20Table%20or%20Matrix%20\(Report%20Builder%20and%20SSRS\).md)  
  
  