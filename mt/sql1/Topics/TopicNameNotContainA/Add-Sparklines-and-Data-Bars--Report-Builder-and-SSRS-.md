---
title: "Add Sparklines and Data Bars (Report Builder and SSRS)"
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
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
caps.latest.revision: 9
manager: mblythe
---
# Add Sparklines and Data Bars (Report Builder and SSRS)
Sparklines and data bars are small, spare charts that convey a lot of information with little extraneous detail. For more information about them, see [Sparklines and Data Bars (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Sparklines-and-Data-Bars--Report-Builder-and-SSRS-.md).  
  
 Sparklines and data bars are most commonly placed in cells in a table or matrix. Sparklines usually display only one series each. Data bars can contain one or more data points. Both sparklines and data bars derive their impact from repeating the series information for each row in the table or matrix.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
### To add a sparkline or data bar to a table or matrix  
  
1.  If you have not done so already, create a table or matrix with the data you want to display. For more information, see [Tables (Report Builder  and SSRS)](../../Topics/TopicNameNotContainA/Tables--Report-Builder--and-SSRS-.md) or [Create a Matrix (Report Builder and SSRS)](../../Topics/TopicNameContainA/Create-a-Matrix--Report-Builder-and-SSRS-.md).  
  
2.  Insert a column in your table or matrix. For more information, see [Insert or Delete a Column (Report Builder and SSRS)](../../Topics/TopicNameContainA/Insert-or-Delete-a-Column--Report-Builder-and-SSRS-.md).  
  
3.  On the **Insert** tab, click **Sparkline** or **Data Bar**, and then click in a cell in the new column.  
  
    > [!NOTE]  
    >  You cannot place sparklines in a detail group in a table. They must go in a cell associated with a group.  
  
4.  In the **Change Sparkline/Data Bar Type** dialog box, click the kind of sparkline or data bar you want, and then click **OK**.  
  
5.  Click the sparkline or data bar.  
  
     The **Chart Data** pane opens.  
  
6.  In the **Values** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want charted.  
  
7.  In the **Category Groups** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want to group by.  
  
     Typically for sparklines and data bars, you will not add a field to the **Series Group** area because you only want one series for each row.  
  
## See Also  
 [Charts (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Charts--Report-Builder-and-SSRS-.md)   
 [Align the Data in a Chart in a Table or Matrix (Report Builder and SSRS)](../../Topics/TopicNameContainA/Align-the-Data-in-a-Chart-in-a-Table-or-Matrix--Report-Builder-and-SSRS-.md)