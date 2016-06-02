---
title: Add or Delete an Indicator (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
---
# Add or Delete an Indicator (Report Builder and SSRS)
  In a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report,indicators are minimal gauges that convey the state of a single data value at a glance. For more information about them, see [Indicators &#40;Report Builder and SSRS&#41;](../Topic/Indicators%20\(Report%20Builder%20and%20SSRS\).md).  
  
 Indicators are commonly placed in cells in a table or matrix, but you can also use indicators by themselves, side\-by\-side with gauges, or embedded in gauges.  
  
 When you first add an indicator, it is by default configured to use percentages as measurement units. The percentage ranges are evenly distributed across members of the indicator set, and the scope of values shown by the indicator is the parent of the indicator such as a table or matrix.  
  
 You can update the values and states of indicators. For more information, see the following topics:  
  
-   [Change Indicator Icons and Indicator Sets &#40;Report Builder and SSRS&#41;](../Topic/Change%20Indicator%20Icons%20and%20Indicator%20Sets%20\(Report%20Builder%20and%20SSRS\).md)  
  
-   [Set and Configure Measurement Units &#40;Report Builder and SSRS&#41;](../Topic/Set%20and%20Configure%20Measurement%20Units%20\(Report%20Builder%20and%20SSRS\).md)  
  
-   [Set Synchronization Scope &#40;Report Builder and SSRS&#41;](../Topic/Set%20Synchronization%20Scope%20\(Report%20Builder%20and%20SSRS\).md)  
  
 Because an indicator is positioned inside the gauge panel, you need to select the indicator instead of the panel when you want to configure the indicator by using the **Indicators Properties** dialog box or the **Properties** pane. The following picture shows a selected indicator in its gauge panel.  
  
 ![rs_GaugePanelWithIndicator](../../Images\Image\ImageNotContaina/rs_GaugePanelWithIndicator.gif "rs_GaugePanelWithIndicator")  
  
> [!NOTE]  
>  Depending on column width and the length of data values, the text in table or matrix cells might wrap and display text on multiple lines. When this occurs, the indicator icon might be stretched and change shape. This can make the indicator icon less readable. Place the indicator inside a rectangle to ensure that the icon is never stretched.  
  
## To add an indicator to a table or matrix  
  
1.  Open an existing report or create a new report that contains a table and matrix with the data you want to display. For more information, see [Tables &#40;Report Builder  and SSRS&#41;](../Topic/Tables%20\(Report%20Builder%20%20and%20SSRS\).md) or [Matrices](Create%20a%20Matrix%20\(Report%20Builder%20and%20SSRS\).md).  
  
2.  Insert a column in your table or matrix. For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](../Topic/Insert%20or%20Delete%20a%20Column%20\(Report%20Builder%20and%20SSRS\).md).  
  
3.  Optionally, on the **Insert** tab, click **Rectangle**, and then click a cell in the new column.  
  
4.  On the **Insert** tab, click **Indicator**, and then click a cell in the new column.  
  
     If you added a rectangle to a cell, click that cell.  
  
5.  In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.  
  
6.  Click **OK**.  
  
7.  Click the indicator. The **Gauge Data** pane opens.  
  
8.  In the **Values** area, in the **\(Unspecified\)** drop\-down list, click the field whose values you want to display as an indicator.  
  
     The indicator is configured to use default values. By default, indicators are configured use percentages as measurement units and the percentage ranges are evenly distributed across the members of the indicator and the value that the indicator conveys uses the scope of the nearest group.  
  
## To delete an indicator to a table or matrix  
  
1.  Right\-click the indicator to delete and click **Delete**.  
  
    > [!NOTE]  
    >  An indicator might be positioned inside a gauge panel that contains other indicators or gauges. If the gauge panels contain multiple items, be sure to click the indicator to delete it, not the gauge panel. If you click and then delete the gauge panel, the gauge panels and all the items in it are deleted.  
  
2.  Click **Delete**.  
  
## See Also  
 [Indicators &#40;Report Builder and SSRS&#41;](../Topic/Indicators%20\(Report%20Builder%20and%20SSRS\).md)  
  
  